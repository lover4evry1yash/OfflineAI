# Offline AI Build Executor
Version: 2.1

## Mission

You are the implementation engine for Offline AI.

Implement exactly ONE task.

Never skip verification.

Never continue to the next task.

Never change project architecture.

---

# Phase 0 — Understand the Project

Read in this exact order:

1. .clinerules/ARCHITECTURE.md

2. .clinerules/VERIFY.md

3. build_plan.yaml

4. state/current_task.json

5. tasks/_template.yaml

6. Current task YAML

Only continue after every file has been read.

---

# Phase 1 — Load Current Task

Determine:

- Current Task
- Dependencies
- Goal
- Inputs
- Outputs
- Acceptance Criteria
- Files to Create
- Files to Modify
- Rollback Strategy

---

# Phase 2 — Dependency Validation

Verify every dependency is complete.

If a dependency is incomplete:

Stop immediately.

Return the missing dependency.

Do not continue.

---

# Phase 3 — Implementation

Implement ONLY the current task.

Create every file listed under:

creates

Modify every file listed under:

modifies

Do not create unrelated files.

Follow ARCHITECTURE.md at all times.

---

# Phase 4 — Self Review

Review your implementation before verification.

Check:

Architecture

Naming

Imports

Complexity

Readability

Code duplication

Exception handling

Logging

If improvements are found:

Fix them before verification.

---

# Phase 5 — Verification

Execute VERIFY.md completely.

Every quality gate must pass.

Every acceptance criterion must pass.

If verification fails:

Execute FAILURE.md.

Stop.

---

# Phase 6 — Success

Update:

build_plan.yaml

state/current_task.json

state/history.json

state/metrics.json

Advance to the next task.

Stop execution.

Never execute another task automatically.

---

# Rules

Implement exactly one task.

Never skip verification.

Never bypass dependencies.

Never violate architecture.

Prefer maintainable code over clever code.

Always leave the repository in a working state.

