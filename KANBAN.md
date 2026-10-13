# Agile Delivery — Kanban

The project follows an **Agile methodology using Kanban** to facilitate continuous delivery, prioritize work, and provide visibility into development progress.

## Board columns

| Stage | Purpose | Entry criteria | Exit criteria |
|---|---|---|---|
| **Backlog** | Identified requirements, ideas, bugs, and technical tasks awaiting prioritization. | Work is captured with enough context to understand the need. | Priority and scope are agreed; acceptance criteria and dependencies are clear. |
| **Ready** | Prioritized work approved and ready for implementation. | The task is actionable, sized where appropriate, and has testable acceptance criteria. | A developer starts work and moves it to In Progress. |
| **In Progress** | Tasks currently being developed. | An owner is assigned and implementation has started. | Implementation is complete, relevant checks pass, and a pull request is ready for review. |
| **In Review** | Completed development work awaiting technical review or testing. | A pull request is open with a summary, test evidence, and linked issue where applicable. | Review comments are resolved, required checks pass, and acceptance criteria are met; otherwise return to In Progress. |
| **Done** | Work that meets its defined acceptance criteria. | Required review and testing are complete, and the change is merged or otherwise delivered according to the repository's workflow. | No further action is required for the current scope. |

## Working agreements

- Keep each card focused on one outcome and link it to relevant issues, pull requests, and documentation.
- Describe the problem and expected outcome; add clear, verifiable acceptance criteria.
- Prioritize the Backlog regularly and move only actionable work into Ready.
- Keep work visible and limit concurrent work in progress. Finish or unblock existing work before starting more.
- Move cards when their actual state changes; do not use column placement to imply work that has not happened.
- If review or testing finds a defect, return the item to In Progress with the required changes documented.
- Use Done only when the acceptance criteria are met and required review/testing is complete.
- Record blockers on the task and identify the next action needed to resolve them.

## Suggested issue template

- **Problem / opportunity:**
- **Expected outcome:**
- **Acceptance criteria:**
- **Dependencies / blockers:**
- **Testing or validation plan:**
- **Related issues / pull requests:**

## Board maintenance

Review priorities and blocked work regularly. Use the board to optimize flow and delivery rather than to measure individual performance.

> This file documents the intended workflow. Create a GitHub Projects board for this repository and configure its status options to match the five stages above; keep issue and pull-request status synchronized with the board.
