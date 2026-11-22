# KnowMyCode

Understand how your code works and what changes when you modify it.

Whether you're joining a team, working in an unfamiliar subsystem, or reviewing AI-generated code, you need to know how the code behaves. KnowMyCode is an open-source project that uses AI to help you trace execution, predict behavior, and check your understanding against the source.

## Explore a codebase

Explore the codebase, understand what it does and use this open source repo to go deeper in specific details. Know what you're working on even if the code will be written by AI. 

**Example:** You just joined the team behind an online store. What happens when a customer clicks **Place order**? Trace how the store checks stock, processes payment, and confirms the order. Then follow what happens when the payment is declined.

## Review a change

Start with a Git diff. Trace the affected flow, compare behavior before and after the change, and identify what to verify before approving it.

**Example:** A pull request moves the order confirmation email to an earlier step in checkout. If the customer's card is declined, could they still get a confirmation email?

<details>
<summary>Reveal the reasoning</summary>

Check where the code sends the email and where it handles a declined payment. If checkout sends the email before checking whether payment succeeded, the customer can receive a confirmation for an order that failed. A test could simulate a declined card and verify that checkout sends no confirmation email.

</details>

## How it will work

1. The CLI gathers relevant code and tests at a specific Git revision. For a review, it also gathers the diff and the source needed to compare behavior.
2. An AI model uses that context to draft a Mermaid flow diagram and questions about what the code does under specific conditions.
3. Predict what happens, reveal the answer, and follow links to the source lines to check the reasoning. The report flags behavior it can't determine from the available code and tests.

## Project status

KnowMyCode is in early development. The first milestone is a Python CLI that produces a Markdown walkthrough or review report. A planned demo will show both workflows using the same online checkout example.

## License

[MIT](LICENSE)
