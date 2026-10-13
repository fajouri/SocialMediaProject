# MVP01 — Agent Decision Record

**Project:** Social Media Platform  
**Repository:** https://github.com/fajouri/SocialMediaProject  
**Parent task:** https://github.com/fajouri/SocialMediaProject/issues/10  
**Purpose:** Canonical reference for Codex Luna and other agents implementing MVP01.  
**Status:** Decisions below reflect the current proposal; customer approval is still pending unless explicitly updated by the project owner.

## 1. Product goal

Deliver a small, browser-based social media application that proves the core journey: an existing, provisioned user logs in, publishes a short text post, and sees the newest posts in a feed. Keep the implementation simple enough to run locally through Docker and maintain as a single application.

## 2. Decisions to treat as fixed for the MVP

| Area | Decision |
|---|---|
| Product | Browser-based web application; no native Android/iOS app. |
| Architecture | Monolith, with clear separation of UI, application/business logic, and persistence. Do not introduce microservices. |
| Frontend | React. |
| Backend | Node.js. |
| Containerization | Docker; the documented local setup must be reproducible. |
| Authentication | Login for existing, provisioned accounts. Public self-registration is not in MVP scope. |
| Posts | Text-only, maximum 300 characters. |
| Feed | Show no more than the 10 newest posts, newest first. |
| Persistence | Users and posts must be stored persistently; data must survive an application restart. |
| Source control and planning | Use this GitHub repository and its linked GitHub Project/Kanban workflow. |
| Delivery style | Incremental, testable changes with issue/PR links and evidence. |

## 3. Functional requirements

- **FR-01 — Login:** A provisioned user can log in with valid credentials. Invalid credentials must not authenticate.
- **FR-02 — Create post:** An authenticated user can submit a text post up to and including 300 characters. A post longer than 300 characters is rejected with understandable validation feedback.
- **FR-03 — Feed:** An authenticated user can see up to 10 posts, ordered newest to oldest.
- **Persistence:** A successfully published post remains available after restarting the application and its supporting services.

## 4. Explicit exclusions

Do not implement these as part of MVP01 unless the project owner changes the scope:

- Public self-registration or user account deletion.
- Editing or deleting posts.
- Browsing older posts or pagination beyond the latest 10.
- User profiles/profile management.
- Likes, comments, sharing, or direct messages.
- Image/video uploads, live streaming, followers, recommendations/AI, notifications, advertisements, or advanced moderation.
- Native mobile applications.
- Microservices, Kubernetes, or other infrastructure not required by the agreed Docker-based MVP.

Keep future ideas in separate backlog issues; do not quietly expand MVP scope.

## 5. Decisions still open — do not invent an answer

The following are **not yet confirmed** in the parent issue. The agent must inspect the repository and existing project artifacts first, then document a proposed choice and rationale. Do not claim the project owner has approved a choice that they have not approved.

1. **Database:** Select a suitable persistent database after inspecting the existing code and constraints. Prefer the simplest reliable option that works in Docker and supports persistent storage. Record the choice, schema/migrations, and backup/reset expectations.
2. **Hosting/deployment target:** Docker is required, but the hosting provider/environment is not selected. Keep local Docker operation independent of a particular cloud. Document any deployment target as proposed until approved.
3. **Account provisioning:** Public registration is excluded. Define a minimal, secure way to create initial users (for example, a documented administrative/bootstrap command or seed mechanism that is safe for development and cannot silently create production default credentials). Never hard-code real secrets or ship a publicly usable default account.
4. **Credentials/session design:** Use established framework/library mechanisms, secure password hashing if passwords are stored, server-side validation, protected routes/API endpoints, and safe session/token handling. Document the actual mechanism chosen.
5. **Customer approval and dates:** Scope approval, target dates, and estimates remain unconfirmed. Do not mark customer approval complete without evidence.

If an open choice blocks implementation, prepare a concise recommendation with trade-offs and ask the project owner for the decision rather than silently treating it as approved. Where a safe implementation detail does not require product-owner input, choose a conventional minimal solution and record it in the architecture documentation.

## 6. Acceptance criteria for MVP01

- [ ] A valid provisioned account can log in.
- [ ] Invalid credentials do not grant access.
- [ ] An authenticated user can publish a post of 1–300 characters (unless the project owner explicitly decides whether empty posts are permitted; recommended behavior is to reject empty/whitespace-only posts).
- [ ] A post over 300 characters is rejected with clear feedback, on both client and server.
- [ ] Unauthenticated users cannot use protected post-creation or feed functionality.
- [ ] Posts are stored persistently and survive an application restart.
- [ ] The feed returns/displays at most 10 posts, newest first, with deterministic ordering for posts sharing a timestamp (for example, a secondary ID/order key).
- [ ] The new post appears in the feed after the relevant refresh/update.
- [ ] The application starts from a clean checkout using documented Docker commands.
- [ ] Required automated tests pass, including authentication/access-control, post-length validation, ordering/limit, and persistence behavior.
- [ ] The README documents configuration, local startup, account provisioning, tests, and deployment assumptions.
- [ ] The agreed customer-accessible deployment and customer validation are completed before the parent issue is marked Done.

## 7. Agent execution rules

1. Read the repository, README, KANBAN.md, current issues, and existing implementation before choosing libraries or replacing files.
2. Preserve the decisions in Section 2. If the current code conflicts, report the conflict and make the smallest safe correction.
3. Prefer the smallest coherent implementation over speculative frameworks, features, or infrastructure.
4. Keep secrets out of source control. Provide an example environment file with placeholders, not real credentials.
5. Validate inputs on the server even if the frontend also validates them. Protect every relevant API endpoint, not just the UI route.
6. Add automated tests for the acceptance criteria. Do not report a test as passing unless it was actually run; record skipped tests and why.
7. Update documentation when setup, architecture, environment variables, or behavior changes.
8. Split work into focused issues/PRs where practical. Link every PR to its issue and include implementation summary, test evidence, and any unresolved decisions.
9. Follow the Kanban stages in KANBAN.md: Backlog → Ready → In Progress → In Review → Done. Do not mark work Done before required review/tests and acceptance evidence exist.
10. Do not deploy, incur paid service costs, or expose the app publicly without explicit authorization for the target environment.
11. Keep the parent issue open until all acceptance criteria and the Definition of Done in issue #10 are satisfied, or clearly document what remains blocked.

## 8. Definition of Done

MVP01 is complete only when the required user journey works end-to-end, the acceptance criteria are evidenced, automated tests pass, Docker startup is repeatable from a clean checkout, the README is usable by another developer, open decisions are recorded/resolved, and customer approval/deployment validation are documented. If deployment or approval remains pending, report the implementation status accurately rather than claiming full completion.

## 9. Project references

- MVP01 parent issue: https://github.com/fajouri/SocialMediaProject/issues/10
- Repository: https://github.com/fajouri/SocialMediaProject
- Project board: https://github.com/users/fajouri/projects/4
- Kanban working agreement: ../KANBAN.md
