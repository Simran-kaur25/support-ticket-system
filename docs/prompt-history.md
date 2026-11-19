# Prompt history

Curated record of iterative, reviewed AI use. SpecStory history (if captured) lives under `.specstory/`.
Entries marked ⚠ have a corresponding row in `docs/ai-mistakes.md`.

| # | Stage | Prompt (short) | AI output summary | Outcome |
|---|---|---|---|---|
| 1 | Plan | Read implementation.md and plan the project | Phased spec-first plan: Cursor hygiene → spec → backend → UI | Accepted — React+Vite, JWT roles, seeded users |
| 2 | Specification | Draft spec/*.md from implementation.md | requirements, data-model, SM, architecture, API, UI, tests, tasks | Accepted with locked search=title+description, page size 10/50 |
| 3 | Hygiene | Add .cursor rules/commands/skills | Glob-scoped .mdc rules, review/generate-tests commands | Accepted |
| 4 | Review ⚠ | Review implementation.md before Phase 1 gate | Flagged Spring Boot 3.5.16 as fully OSS-EOL (support ended June 30, 2026) | Rejected — switched to Spring Boot 4.1.x; ADR added to `spec/decisions.md` |
| 5 | Review ⚠ | Review implementation.md before Phase 1 gate | Test-strategy said "6 valid transitions"; actual allow-list has 5 | Rejected — corrected in spec/state-machine.md, spec/test-strategy.md, .cursor/rules/state-machine.mdc; made state-machine.md the single source of truth |
| 6 | Review | Review PATCH /tickets/{id} authorization | Role + field + precondition crammed into one table cell | Edited — split into explicit role/field/precondition matrix in api-contract.md |
| 7 | Review | Audit for scope creep vs original brief | Auth/roles not in original assignment text | Edited — added "Assumptions & Additions" section to spec/requirements.md; added login/role-scoping to acceptance checklist |
| 8 | Specification | Small functional additions (ref code, unassign semantics, internal comments, resolved/closed timestamps, sort allow-list) | Additive columns/params, no schema rewrite | Accepted — folded into data-model.md and api-contract.md before Phase 1 sign-off |
| 9 | Implementation | Implement TicketStateMachine + API | Single allow-list in TicketStatus; 409 InvalidTransitionException | Accepted after exhaustive cartesian unit tests |
| 10 | Testing ⚠ | Generate tests for TicketController/IT | MockMvc + Testcontainers; SM 409 cases; customer isolation 404 | Edited — AI's first pass didn't isolate seeded data between tests (customer B could see customer A's ticket count); added second seeded customer + DB wipe between tests |
| 11 | Frontend | React Vite login/list/detail | JWT sessionStorage, valid-next status buttons, fieldErrors | Accepted |
| 12 | Docs | README + ADR | JWT ADR, env placeholders, swagger link | Accepted |

