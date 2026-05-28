# agent-hub

<p align="center">
  English | <a href="README.md">中文</a>
</p>

`agent-hub` is this workspace's self-owned AI Agent project management hub.

Repository: [TzexZhang/agent-hub](https://github.com/TzexZhang/agent-hub)

The current scope is intentionally small:

- `agent-hub`: parent management project for project mapping, capability
  assignment, and cross-project configuration.
- `github-sentinel`: the only planned child project, reserved for GitHub
  repository tracking, update retrieval, notification, and report generation.

`agent-hub` records project mapping, ownership, capability assignment, runtime
intent, GitHub repository tracking rules, and report configuration. Child
projects keep their own implementation files.

## Purpose

Use `agent-hub` as the source of truth for the current workspace's agent project
mapping. It answers these questions:

- Which child projects exist?
- Where are they located locally?
- Which capabilities are assigned to them?
- Which GitHub repositories should they track?
- Which runtime and report settings belong to them?

## Current Project Map

```text
program/
  agent-hub/
    README.md
    README-EN.md
    PROJECT_MANAGEMENT.md
    projects.yaml
    LICENSE
  github-sentinel/
```

## Current Scope

Only `github-sentinel` is registered as a child project. Other agent projects
are outside the current scope and should not be added until the scope is
explicitly expanded.

## Configuration Ownership

Use `agent-hub` for:

- child-project identity and local path mapping;
- capability catalog and capability assignment;
- owner, lifecycle status, and operational notes;
- GitHub repository tracking rules;
- report cadence, language, and output target;
- environment variable names required by child projects.

Use `github-sentinel` for:

- implementation code;
- dependency and package manager files;
- tests;
- service entrypoints;
- prompts;
- deployment files;
- generated runtime outputs.

## Files

- `README.md`: Chinese project overview.
- `README-EN.md`: English project overview.
- `PROJECT_MANAGEMENT.md`: project management guide.
- `projects.yaml`: formal project mapping configuration.
- `LICENSE`: MIT License.

## License

This project is licensed under the MIT License. See `LICENSE`.
