<!-- TOC --><a name="-ground-rules"></a>
## 📜 Ground Rules

Before you start contributing to `kokaq`, please ensure you align with the following principles and practices. These guidelines are essential for maintaining the reliability, clarity, and long-term maintainability of the project.

+ [🚨 Avoid Breaking Public APIs](#-avoid-breaking-public-apis)
+ [📦 Minimize Dependencies](#-minimize-dependencies)
+ [✅ Unit Tests Are Mandatory](#-unit-tests-are-mandatory)


<!-- TOC --><a name="-avoid-breaking-public-apis"></a>
### 🚨 Avoid Breaking Public APIs
Stability matters. The core library may be embedded into other systems, so any breaking change to exported functions, types, or behaviors must be:
- Discussed in a GitHub Issue or Discussion beforehand.
- Clearly described in the PR title and body.
- Accompanied by migration guidance (when possible).

Semantic versioning will be used to manage compatibility in tagged releases.

<!-- TOC --><a name="-minimize-dependencies"></a>
### 📦 Minimize Dependencies
`kokaq` modules are meant to be lightweight, embeddable, and safe for use in critical paths. That means:
- Use only standard library packages whenever possible.
- Avoid adding dependencies for convenience.
- Any third-party package must have:
  - A clear benefit that outweighs the cost.
  - A long-term maintenance track record.
  - Minimal transitive dependency bloat.

If you’re unsure whether to add a package, open a discussion first.

<!-- TOC --><a name="-unit-tests-are-mandatory"></a>
### ✅ Unit Tests Are Mandatory
All new features and bug fixes must be accompanied by unit tests. This ensures:
- Correctness of the code you’re introducing.
- That regressions are caught early as the project evolves.
- Clear intent for how the code should behave.

> Use the standard testing package. Tests should be deterministic, fast, and self-contained (no reliance on external services or network).

If you're contributing low-level core logic like scheduling or prioritization, you’re expected to include tests that verify edge cases and boundary conditions.

> Generate TOC with https://github.com/derlin/bitdowntoc