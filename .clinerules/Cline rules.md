# Offline AI Workspace Rules

## Environment

- Operating System: Windows 11
- Shell: Windows PowerShell
- Python: 3.12
- Project Root: Current workspace
- LM Studio provides the OpenAI-compatible API.

---

## General Behavior

- Think before acting.
- Do not repeatedly call the same tool if it already failed.
- If a command fails, analyze the cause before retrying.
- Never loop on identical tool calls.
- Stop after completing the requested task.

---

## File Operations

- Never inspect the entire project unless explicitly requested.
- Never recursively scan the repository unless asked.
- Create only the files requested.
- Modify only the files requested.
- Never create extra files or folders.
- Never overwrite existing code unless instructed.

---

## Shell Commands

Generate commands compatible with Windows PowerShell.

Never use:

- mkdir -p
- && (unless PowerShell 7+ is confirmed)
- Linux paths
- bash syntax
- sh syntax

Prefer:

- New-Item
- Set-Content
- Copy-Item
- Move-Item
- Remove-Item

One command per line is preferred.

---

## Python Code

- Python 3.12
- Use type hints.
- Use dataclasses where appropriate.
- Keep modules focused on a single responsibility.
- Prefer pathlib over os.path.
- Follow PEP 8.

---

## Development Style

Build incrementally.

Never scaffold the entire application in one request.

Each task should:

- Create one module.
- Complete one feature.
- Stop.

---

## Architecture

The project is a software development automation framework.

Python is the orchestrator.

The AI only performs reasoning tasks such as:

- Planning
- Code generation
- Code review

Python performs deterministic tasks such as:

- File operations
- Repository indexing
- Patch application
- Running builds
- Validation

Do not introduce unnecessary abstractions.