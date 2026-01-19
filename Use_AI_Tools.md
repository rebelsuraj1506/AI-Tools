# Junior Developer Workflow: AI Collaboration & Debugging (2026)

This document outlines the standard operating procedure for using AI tools effectively and approaching production-level issues as a fresher.

## 🤖 1. Daily Workflow: AI as a Collaborative Partner
In 2026, AI is not a code-generator; it is a **senior mentor** available 24/7. Avoid asking for "full solutions" to ensure you are actually learning the logic.

### Prompting for Logic, Not Just Syntax
When you need help, focus on the **how** and **why** rather than just the "what."
*   **Weak Prompt:** "Write a prime number function."
*   **Strong Prompt:** "Write a Python function to check if a number is prime, optimized for numbers up to 10,000. Explain the time complexity of your approach."

### "Rubber Ducking" with AI
When you hit a wall, use AI to unblock your thinking without spoiling the answer.
*   **The Strategy:** Paste your incomplete code and say: *"I'm trying to solve this by sorting the input, but I feel stuck. Don't give me the code; give me a high-level hint about a better data structure I could use."*

### Real-time Learning
Leverage IDE-integrated tools like [GitHub Copilot](https://github.com) or [Cursor](https://www.cursor.com) for instant clarification:
*   **Explain Feature:** Highlight unfamiliar syntax or legacy code, right-click, and select **"Explain"** for a plain-English breakdown.
*   **Documentation Search:** Use AI to find specific methods in the latest 2026 documentation instead of scrolling through long manual pages.

---

## 🐞 2. Debugging Example: The "Broken API" Case
If a user reports they cannot log in, follow this AI-assisted debugging path:

### Step 1: Pinpoint the Error
Before opening an AI chat, find the raw error message in your terminal or [Chrome DevTools](https://developer.chrome.com).
*   **Example:** `ReferenceError: user_data is not defined`

### Step 2: Provide Full Context
Context is king. Never paste an error in isolation. 
*   **The Prompt:** *"I'm getting a `ReferenceError: user_data is not defined` in the function below. It should be pulling from my login route. Can you explain where the logic breaks?"* [Paste Function Here]

### Step 3: Analyze "Invisible" Production Issues
If the code looks perfect but fails in the live environment:
*   **AI Simulation:** Ask: *"Here is my login logic. Can you list five edge cases (like empty strings, SQL injection attempts, or special characters) that might cause this to fail in production?"*
*   **Trace the Flow:** Use tools like [Sentry AI](https://sentry.io) to feed "session data" into your AI agent so it can visualize exactly what the user did before the crash.

---

## ✅ 3. The Fresher Checklist for Production Issues
When a bug hits production, follow this rigorous workflow to ensure a safe fix:

1.  **Isolate:** Feed the AI one function at a time to avoid "context drift" or confusion.
2.  **Verify:** If the AI suggests a fix (e.g., *"You forgot a flush() call"*), research the function on [MDN](https://developer.mozilla.org) or [Stack Overflow](https://stackoverflow.com) to understand what it does.
3.  **Test:** Ask the AI: *"Write a Unit Test for the fix you just proposed to ensure it doesn't break existing functionality."*
4.  **Audit:** Double-check that the AI isn't hallucinating non-existent libraries or suggesting outdated 2024/2025 syntax that is deprecated in 2026.
