# .NET baseline

- Use feature-oriented namespaces and directories under `src`, with corresponding tests under `tests`.
- Enable nullable reference types, .NET analyzers, code-style enforcement, and warnings as errors.
- Use a root `.editorconfig`; prefer mandatory braces and explicit method blocks.
- Use one class, interface, enum, struct, record, or delegate per matching `.cs` file. Partial types may use descriptive names such as `ArticleEndpoints.Admin.cs`.
- Propagate cancellation across asynchronous boundaries and avoid sync-over-async.
- Verify restore, formatting, analyzer-clean Release build, tests, feature coverage, and publish or production build when applicable.
