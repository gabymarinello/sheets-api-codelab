# GitHub Copilot Instructions

## Project Overview
This repository is part of the ASCENIX / BMOPS / BEAUTIFUL-MINDS ecosystem — an enterprise-grade multi-platform workspace spanning iOS/macOS, Google Workspace, web services, and AI agent orchestration.

## General Guidelines
- Write clean, self-documenting code. Add comments only when logic is non-obvious.
- Follow existing naming conventions found in the codebase — do not introduce new patterns without reason.
- Prefer explicit over implicit. Avoid magic numbers; use named constants.
- Prioritize security: never hardcode secrets, tokens, API keys, or credentials.
- All new features must be testable. Prefer dependency injection and modular design.
- When multiple approaches exist, prefer the one already used in this repo.

## Language & Framework Preferences
### Swift / iOS / macOS
- Target Swift 5.9+ and the latest stable SDK unless otherwise specified.
- Use SwiftUI for new UI; UIKit only when SwiftUI cannot accomplish the task.
- Prefer `async/await` over callback-based concurrency.
- Use `Codable` for serialization. Prefer `Identifiable` + `Hashable` for data models.
- Follow Apple Human Interface Guidelines.

### TypeScript / JavaScript
- Prefer TypeScript over plain JavaScript for all new files.
- Use ESModules (`import/export`), not CommonJS.
- Async operations use `async/await`; avoid raw `.then()` chains.
- Use strict TypeScript (`"strict": true`).

### Python
- Target Python 3.10+ unless constrained by the runtime environment.
- Use type hints and dataclasses/Pydantic for structured data.
- Prefer `pathlib` over `os.path`, `httpx` over `requests` for async work.

### Google Workspace / Apps Script
- Apps Script: use V8 runtime runtime features. Avoid deprecated methods.
- Use typed JSDoc for all functions and parameters.
- Use `SpreadsheetApp`, `DriveApp`, `GmailApp` etc. only via service objects — avoid global mutations.

### Go
- Follow standard Go idioms: error wrapping, defer for cleanup, context propagation.
- Prefer interfaces over concrete types in function signatures.

## BMOPS / ASCENIX Conventions
- Repo numbering prefix (e.g. `02.00.00__`) encodes the module tier; preserve it.
- Agent repos (`7x.00.00__ASCENIX_AGENT_*`) contain AI agent configurations — treat YAML/JSON configs as first-class code.
- Use the `ASCENIX_` namespace prefix for shared utilities.
- Enterprise data must never be logged in plain text.

## AI Agent Development
- When working in agent repos, keep prompts modular and parameterized.
- Avoid hardcoding environment-specific values in prompt templates.
- Prefer deterministic tool calls over open-ended LLM generation when correctness matters.

## Git & Collaboration
- Write imperative commit messages: `Add feature`, `Fix bug`, `Refactor module`.
- Keep PRs focused; one logical change per PR.
- Update `README.md` and docs when changing public APIs or behavior.
