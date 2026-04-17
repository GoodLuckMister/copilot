# Global Copilot Instructions

## General Behavior
- Always respond in English. Exclusion: Ukrainian/українська.
- Do not do anything that wasn't asked.
- Prefer concise, production-ready output over verbose explanations.
- Use modern language features and idioms appropriate to the current project.
- Follow the principle of least surprise in all suggestions.
- Use available skills, agents, and instruction files when present.

## Architecture & Design
- Follow SOLID principles: single responsibility, open/closed, Liskov substitution, interface segregation, dependency inversion.
- Prefer composition over inheritance.
- Separate concerns: keep business logic, data access, presentation, and configuration in distinct layers.
- Design for testability — avoid tight coupling and hidden dependencies.
- Favor stateless components; isolate and minimize mutable state.
- Use dependency injection; never hardcode concrete implementations in business logic.
- Prefer idempotent operations where applicable.
- Keep interfaces small, focused, and well-defined.

## Code Quality
- Write self-documenting code with clear, descriptive names for variables, functions, types, and files.
- Keep functions short — each should do exactly one thing.
- Avoid magic numbers and magic strings; use named constants.
- Eliminate dead code, commented-out blocks, and unused imports.
- Never duplicate logic — extract shared behavior into reusable units.
- Reduce nesting depth; prefer early returns and guard clauses.
- Follow the project's existing code style and conventions. If none exist, suggest widely adopted community standards.
- Use linters and formatters as defined by the project. If none are configured, recommend appropriate ones.

## Security (Always Apply)
- Never hardcode secrets, API keys, tokens, passwords, or certificates.
- Use environment variables or a secrets manager for all credentials.
- Always validate, sanitize, and bound-check all external input.
- Use parameterized queries for all database access — never concatenate user input into queries.
- Prefer encrypted channels for all network communication.
- Apply the principle of least privilege to all access: files, APIs, databases, hardware peripherals.
- Never trust client-side validation alone; always enforce on the server or controller side.
- Avoid exposing internal system details in error messages or logs.
- Never log sensitive data (credentials, tokens, PII, cryptographic material).

## Error Handling
- Never silently swallow errors.
- Handle errors at the appropriate layer — don't catch what you can't meaningfully handle.
- Use structured, typed error representations; avoid raw strings for error signaling.
- Provide context with every error: what failed, where, and with what input.
- Distinguish between recoverable and fatal errors. Recover gracefully when possible; fail fast and loud when not.
- Clean up resources (connections, handles, memory, peripherals) in all error paths.

## Testing
- Write tests alongside new code — not as an afterthought.
- Structure tests clearly: setup → action → assertion.
- Test behavior and outcomes, not internal implementation details.
- Mock external dependencies; never call real services, hardware, or networks in unit tests.
- Cover edge cases, boundary values, invalid inputs, and failure paths.
- Keep tests independent, deterministic, and fast.
- Name tests to describe the scenario and expected result.

## Documentation
- Add clear comments/docstrings to all public functions, types, and modules.
- Explain *why*, not *what* — the code shows what, comments explain intent.
- Include usage examples in docstrings when the usage is non-obvious.
- Document assumptions, constraints, limitations, and side effects.
- Keep documentation co-located with the code it describes.
- Update documentation when the related code changes.

## Shell & Scripting
- Write portable scripts unless platform-specific features are explicitly required.
- Enable strict error handling at the top of every script.
- Quote all variable expansions to prevent word splitting and globbing.
- Validate required inputs and environment before executing destructive operations.
- Prefer scripts that are idempotent and safe to re-run.

## Git & Version Control
- Write conventional commit messages: `type(scope): description`.
- Types: feat, fix, docs, style, refactor, test, chore, ci.
- Keep commits atomic — one logical change per commit.
- Never commit secrets, generated artifacts, build outputs, or large binaries.

## Build, Packaging & Deployment
- Pin all dependency versions for reproducible builds.
- Separate build-time and runtime dependencies.
- Minimize the size and attack surface of deployable artifacts.
- Never run services or processes with elevated privileges unless absolutely required.
- Use ignore files to exclude unnecessary artifacts from version control and packages.
- Automate build, test, and deployment steps — avoid manual procedures.

## Firmware & Embedded Considerations
- Minimize dynamic memory allocation; prefer static or pool-based allocation.
- Be explicit about data sizes, alignment, and endianness.
- Guard against integer overflow, underflow, and truncation.
- Protect shared resources with appropriate synchronization primitives.
- Handle hardware peripheral failures gracefully — never assume hardware is reliable.
- Document memory layout, register maps, and timing constraints.
- Avoid blocking operations in interrupt handlers; keep them minimal and fast.
- Validate all inputs from external buses, sensors, and communication interfaces.
- Design for safe degradation: define what happens when components fail.
- Use watchdog timers and self-check mechanisms for critical systems.

## Performance & Resource Awareness
- Avoid premature optimization — write correct, clear code first; optimize with evidence.
- Be conscious of memory, CPU, power, and bandwidth constraints.
- Prefer algorithms and data structures appropriate to the data size and access pattern.
- Avoid unnecessary allocations, copies, and I/O in critical paths.
- Cache results of expensive computations when the data is stable.
- Release resources (connections, handles, files, locks) as soon as they are no longer needed.

## Logging & Observability
- Use structured, leveled logging (debug, info, warn, error).
- Include correlation identifiers for tracing across boundaries.
- Log at the appropriate level — don't flood logs with noise.
- Never log sensitive or personally identifiable information.
- Make systems observable: expose health checks, metrics, and diagnostics where applicable.

## Configuration Management
- Externalize all environment-specific values — never embed them in code.
- Provide sensible defaults with the ability to override.
- Validate configuration at startup; fail fast on invalid or missing values.
- Document every configuration option and its expected format.

## AI Agent Behavior
- When asked to fix something, explain the root cause before providing the fix.
- When generating files, always include the full file path.
- Prefer editing existing code over rewriting entire files.
- When multiple approaches exist, briefly state the tradeoff and recommend one.
- Do not introduce new dependencies without stating it explicitly.
- Respect existing project patterns — match the style already in use.
