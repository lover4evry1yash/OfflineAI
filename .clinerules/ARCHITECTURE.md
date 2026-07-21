# Offline AI Architecture
Version: 2.0

---

# Purpose

Offline AI is an autonomous software engineering assistant designed to
analyze repositories, plan work, generate code, validate changes,
apply patches and remember previous executions while running completely
offline using LM Studio.

Every module has exactly one responsibility.

Modules communicate only through well-defined public interfaces.

---

# High Level Architecture

Task
    │
    ▼
Repository
    │
    ▼
Planner
    │
    ▼
Prompt Builder
    │
    ▼
LM Studio
    │
    ▼
Coder
    │
    ▼
Reviewer
    │
    ▼
Validator
    │
    ▼
Patcher
    │
    ▼
Runner
    │
    ▼
Memory

---

# Core Layer

Directory:

offline_ai/core/

Purpose:

Shared infrastructure.

Contains:

config.py

exceptions.py

logger.py

context.py

lmstudio.py

router.py

workflow.py

Rules:

Must never depend on AI modules.

Must never import repository layer.

May be imported by every other module.

---

# Repository Layer

Directory:

offline_ai/repository/

Purpose:

Understand the source code.

Responsibilities:

Scan repository.

Read files.

Index repository.

Search symbols.

Search imports.

Search classes.

Search functions.

Must never call LM Studio.

Must never generate code.

Only provides repository knowledge.

---

# AI Layer

Directory:

offline_ai/ai/

Purpose:

Reason about software.

Modules:

planner.py

prompt_builder.py

coder.py

reviewer.py

Responsibilities:

Understand tasks.

Create implementation plans.

Assemble prompts.

Generate code.

Review generated code.

Rules:

Never modify files directly.

Never patch repositories.

Never execute shell commands.

---

# Engine Layer

Directory:

offline_ai/engine/

Purpose:

Apply and verify AI output.

Modules:

patcher.py

validator.py

runner.py

Responsibilities:

Apply code changes.

Run verification.

Execute commands.

Return execution results.

Rules:

Never generate code.

Never plan architecture.

Never build prompts.

---

# Memory Layer

Directory:

offline_ai/memory/

Purpose:

Persist knowledge.

Responsibilities:

Task history.

Execution history.

Statistics.

Previous failures.

Previous successes.

Rules:

Never execute code.

Never call LM Studio.

Only read and write memory.

---

# Data Flow

Repository

↓

Planner

↓

Prompt Builder

↓

LM Studio

↓

Generated Code

↓

Validator

↓

Patcher

↓

Runner

↓

Memory

---

# Dependency Rules

Core

↑

Repository

↑

AI

↑

Engine

↑

Memory

Lower layers must never import higher layers.

No circular imports.

---

# General Coding Rules

Python 3.12

UTF-8

pathlib

dataclasses(slots=True)

Type hints everywhere.

Docstrings for public APIs.

No TODO comments.

No placeholder code.

No global mutable state.

Small functions.

Single Responsibility Principle.

Dependency Injection preferred.

Composition over inheritance.

Fail fast.

Explicit exceptions.

Readable code over clever code.

---

# Error Handling

Never silently ignore exceptions.

Raise meaningful custom exceptions.

Log every unexpected failure.

Never expose stack traces to users.

---

# Logging

Every important operation must log:

Start

Success

Failure

Duration

---

# Validation

Every implementation must:

Compile.

Import successfully.

Pass verification.

Satisfy acceptance criteria.

---

# Build System

Execution order is controlled only by:

build_plan.yaml

Task definitions.

State files.

Never skip dependencies.

Never execute multiple tasks.

Stop after successful completion.

---

# Future Expansion

New capabilities should be added as new tasks.

Examples:

Git integration

Unit testing

Benchmarks

AI Reviewer

Vector Memory

Multi-model routing

Plugin system

Web UI

Do not modify existing architecture unless necessary.

Extend rather than replace.

---

# Guiding Principle

Every module should do one thing well.

Keep responsibilities isolated.

Prefer maintainability over cleverness.

The architecture should remain predictable as the project grows.

