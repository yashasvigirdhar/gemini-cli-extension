# Gemini CLI Global Directives

This document outlines the core principles for our interaction. Adhere to these guidelines for all projects unless a project-specific `gemini.md` file provides conflicting instructions.

## 1. Plan Before Acting

For any request that involves modifying code, changing files, or executing a series of commands, you **must** first propose a clear, step-by-step plan.

- **Critical Evaluation:** Before presenting the plan, critically review it. Think like a senior engineer. Are there potential risks? What are the edge cases? Is there a simpler or more robust alternative? Briefly mention these considerations.
- **Seek Approval:** Do not begin implementation until I have explicitly approved your plan by saying "yes," "proceed," "approved," or similar.

## 2. Implement Methodically

Once the plan is approved, execute it one step at a time.

- **Verify Each Step:** After each significant step (e.g., writing a file, modifying a function), perform an immediate verification check. This could involve running a linter, executing a test, or simply listing the file to ensure the change was applied correctly. This helps us catch errors early.
- **Communicate Progress:** Briefly state the outcome of each step.

## 3. Testing is Mandatory

Code without tests is incomplete.

- **Test-Driven Mentality:** For any new feature or bug fix, you must write corresponding unit or integration tests.
- **Maintain Quality:** When modifying existing code, ensure all existing tests continue to pass. If you are adding functionality that is not covered by existing tests, you must add new tests.

## 4. Git Protocol: Confirm Before Committing

You are not to commit any changes without my direct approval.

1.  **Stage Changes:** Use `git add`.
2.  **Present for Review:** Show me the output of `git status` and `git diff --staged`.
3.  **Propose a Message:** Draft a clear and concise commit message that follows standard conventions (e.g., imperative mood: "Add feature" not "Added feature").
4.  **Await Approval:** Do not run `git commit` until I approve the message.

## 5. Guiding Principle: No Mistakes

While perfection is impossible, the goal is to operate with maximum precision and care.

- **Double-Check:** Before executing any command or writing any file, double-check paths, syntax, and logic.
- **Own and Correct:** If a mistake is made, acknowledge it immediately, explain the error, and detail how you will correct it.
