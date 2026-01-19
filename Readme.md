# 🚀 Engineering SOP: Incident Response & AI-Assisted Development

This guide outlines the mandatory procedures for handling production bugs and the standardized workflow for using AI Code Assistants within our engineering team.

---

## 🛠 1. Production Bug Remediation (Example Case)

### **Scenario: The "Null Name" Signup Crash**
**Issue:** A deployment caused the "Welcome Email" service to crash because it received an empty string (`""`) or `null` instead of a user's name.

### **Phase A: Immediate Containment (The "Stop the Bleed" Step)**
1.  **Rollback First:** In 2026, we do not "fix forward" during a crash. Use the [Vercel Dashboard](https://vercel.com) or [AWS CloudFormation](https://aws.amazon.com) to revert to the previous stable build (e.g., `v1.0.4` to `v1.0.3`).
2.  **Verify Stability:** Confirm that the production error rate in [Sentry](https://sentry.io) has returned to zero.

### **Phase B: Diagnosis & The Hotfix**
1.  **Reproduction:** Create a failing test case locally. 
    ```javascript
    // Example: Trigger the failure in your local environment
    test('should not crash when name is missing', () => {
      expect(sendWelcomeEmail(null)).not.toThrow();
    });
    ```
2.  **The Fix:** Implement defensive programming.
    ```javascript
    // Use Nullish Coalescing (??) to provide a fallback
    const greetingName = user.name?.trim() || "Valued Member";
    ```
3.  **Deployment:** Push the fix to a `hotfix/` branch, pass CI/CD checks, and merge to `main`.

---

## 🤖 2. AI Code Editing Workflow (The "Human-in-the-Loop" Standard)

AI assistants (Cursor, GitHub Copilot, Windsurf) are powerful but prone to "hallucinations." Follow these steps for every edit:

### **Step 1: Priming Context**
Don't ask for a fix in a vacuum. Provide the AI with the **Model** and **Schema**.
*   **Good Prompt:** *"I am using React with Zod for validation. Based on `userSchema.ts`, update the `SignupForm.tsx` to prevent empty strings in the name field."*

### **Step 2: Planning Mode**
Before allowing the AI to write code, ask for a plan.
*   **Action:** Switch your AI assistant to "Architect" or "Chat" mode and say: *"Explain your plan to fix this before you modify any files."* 
*   **Goal:** Verify the AI isn't introducing a breaking change to a shared component.

### **Step 3: The Diff Review (Mandatory)**
When applying AI-generated code, review the **Diff** (the Red/Green lines):
*   **Check for Deletions:** Did the AI accidentally delete an important `import` or `useEffect` hook?
*   **Check for "Fake" Libraries:** Ensure the AI didn't invent a library that doesn't exist in our `package.json`.

### **Step 4: Autonomous Testing**
After the AI edits the code, ask it to write its own verification test:
*   *"Now write a Playwright end-to-end test to ensure the signup button is disabled if the name field is empty."*

---

## 📊 Summary for Freshers (2026 Edition)

| Action | Traditional Way | 2026 AI-Assisted Way |
| :--- | :--- | :--- |
| **Bug Detection** | Checking logs manually | [Datadog](https://www.datadog.com) AI Anomaly Alerts |
| **Bug Fixing** | Searching StackOverflow | AI Chat with codebase indexing (@Codebase) |
| **Code Review** | Senior Dev reads line-by-line | AI-diff summary + Senior Dev oversight |
| **Safety Net** | Manual Testing | Automated Canary Deployments & Feature Flags |

---

## 📝 Post-Incident Checklist
- [ ] Was the bug reproduced locally?
- [ ] Did the AI-generated fix follow our [Style Guide](https://google.github.io)?
- [ ] Is there a new unit test to prevent this specific bug from returning?
- [ ] Did you update the Documentation/README if logic was changed?

---
*Created by the Engineering Operations Team | January 2026*
