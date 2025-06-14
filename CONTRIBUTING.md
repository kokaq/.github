# Contributing to `kokaq`

First off, thank you for taking the time to contribute! 🎉  

* [📜 Ground Rules](#-ground-rules)
   + [🎯 Follow Go Idioms and Best Practices](#-follow-go-idioms-and-best-practices)
   + [🚨 Avoid Breaking Public APIs](#-avoid-breaking-public-apis)
   + [📦 Minimize Dependencies](#-minimize-dependencies)
   + [✅ Unit Tests Are Mandatory](#-unit-tests-are-mandatory)
* [🔧 Development Setup](#-development-setup)
   + [🧰 Prerequisites for Development Setup](#-prerequisites-for-development-setup)
   + [🚀 Getting Started](#-getting-started)
      - [1. Clone all repositories into the same folder:](#1-clone-all-repositories-into-the-same-folder)
      - [2. Initialize `go.work`](#2-initialize-gowork)
   + [Debug Mode (Default Dev)](#debug-mode-default-dev)
   + [Release Mode (CI / Production)](#release-mode-ci-production)
* [🧪 Testing & Coverage](#-testing-coverage)
   + [Tips](#tips)
* [🔄 Creating a Pull Request](#-creating-a-pull-request)
* [🙋 Support & Questions](#-support-questions)

<!-- TOC end -->


<!-- TOC --><a name="-ground-rules"></a>
## 📜 Ground Rules

Before you start contributing to `kokaq`, please ensure you align with the following principles and practices. These guidelines are essential for maintaining the reliability, clarity, and long-term maintainability of the project.

<!-- TOC --><a name="-follow-go-idioms-and-best-practices"></a>
### 🎯 Follow Go Idioms and Best Practices
Your code should feel familiar to any experienced Go developer. To achieve this:
- Use idiomatic naming: `NewX` for constructors, `Do` for actions, etc.
- Structure packages with clear responsibilities (no god packages).
- Apply `gofmt`, and run `golangci-lint run` before submitting a PR.
- Prefer explicitness over magic — simplicity is a feature.

> A good rule of thumb: if you’re unsure whether a pattern is idiomatic in Go, check [Effective Go](https://golang.org/doc/effective_go.html) or existing code in the Go standard library.

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


<!-- TOC --><a name="-development-setup"></a>
## 🔧 Development Setup

<!-- TOC --><a name="-prerequisites-for-development-setup"></a>
### 🧰 Prerequisites for Development Setup

Before you start working on `kokaq`, ensure your development environment meets the following requirements:

**🛠 Required Tools**

| Tool | Version | Description |
| ---- | --------|------------ |
| Go | >= 1.24 | Required to build, test, and lint the project |
| Make | Any UNIX make | Used to run common development commands |
| Git | Latest stable | For source control and cloning repositories |
| Visual Studio Code | Latest stable | IDE |
| GolangCI-Lint | v1.54+ | For running static code analysis (make lint) |

> Optional: Install via [golangci-lint installation guide](https://golangci-lint.run/usage/install/)

**📦 Go Environment Setup**


This repo is part of a modular Go project containing multiple services and modules:
- `kokaq-core` is the heart of `kokaq`. It provides the foundational logic and data structures for enabling true, weight-based prioritization across distributed systems.
- `kokaq-protocol` contains the canonical tcp protocol definitions for kokaq server.
- `kokaq-server` is the production server component of `kokaq`. It hosts APIs, integrates with backend storage, exposes metrics, and runs the scheduling/dispatch logic 
  - depends on `kokaq-core`, `kokaq-protocol`
- `kokaq-client` provides official SDKs to interact with `kokaq` server via REST and gRPC.
  - depends on `kokaq-core`, `kokaq-protocol`

<!-- TOC --><a name="-getting-started"></a>
### 🚀 Getting Started

<!-- TOC --><a name="1-clone-all-repositories-into-the-same-folder"></a>
#### 1. Clone all repositories into the same folder:

```bash
mkdir kokaq && cd kokaq
git clone https://github.com/kokaq/kokaq-core.git
git clone https://github.com/kokaq/kokaq-protocol.git
git clone https://github.com/kokaq/kokaq-server.git
git clone https://github.com/kokaq/kokaq-client.git
```
<!-- TOC --><a name="2-initialize-gowork"></a>
#### 2. Initialize `go.work`

```bash
go work init ./kokaq-core ./kokaq-protocol
```

It will generate:
```go
// go.work
go 1.21

use (
    ./kokaq-core
    ./kokaq-protocol
)

```

<!-- TOC --><a name="debug-mode-default-dev"></a>
### Debug Mode (Default Dev)
Just use go.work. No replace needed. Modules will resolve locally.

<!-- TOC --><a name="release-mode-ci-production"></a>
### Release Mode (CI / Production)
You want to:
- Use published Git tags like `github.com/kokaq/core/v1`
- Remove or ignore go.work

<!-- TOC --><a name="-testing-coverage"></a>
## 🧪 Testing & Coverage
All logic must be covered by:

- ✅ Unit tests using the testing package
- 🌀 Fuzzing for unmarshaling/serialization paths (if applicable)
- 🏎️ Benchmarks for hot-path logic (e.g. schedulers)

<!-- TOC --><a name="tips"></a>
### Tips
> 
> - Use `go test ./...` from any module.
> - Modify code in `kokaq-core/`, and `kokaq-protocol` will pick up changes immediately.

<!-- TOC --><a name="-creating-a-pull-request"></a>
## 🔄 Creating a Pull Request
Follow these steps to contribute code to the kokaq-core repository:

1. Fork the Repository
If you don’t have write access:
- Click Fork on the top-right of kokaq-core.
- Clone your fork:

```bash
git clone https://github.com/your-username/kokaq-core.git
cd kokaq-core
```

If you have write access, clone the repo directly and work off the `main` branch.


2. Create a New Branch
Always branch from main:

```bash
git checkout -b feat/scheduler-prioritization
git checkout -b fix/etcd-client-config-errors
git checkout -b test/file-utils-unit-test-and-coverage
```
Use a descriptive name based on the feature or fix you're working on.

3. Make Your Changes
- Follow all 📜 Contribution Principles
- Write or update unit tests
- Validate your code:

```bash
make test    # Runs tests with coverage and race detection
make lint    # Runs static analysis via golangci-lint
```

3. Use [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) to allow automatic changelog generation:

```
feat(scheduler): add weighted fair implementation
fix(storage): correct dequeue starvation logic
test: add fuzzing for wireframe decoding
```

```bash
git add .
git commit -m "feat(scheduler): add priority aging strategy"
```

4. Push and Open a PR

```bash
git push origin feat/scheduler-prioritization
```

Then:
- Go to your fork on GitHub
- Click "Compare & pull request"
- Fill out the PR template (description, motivation, test coverage, etc.)
- Link issues (e.g., `Fixes #42`) if applicable

5. Participate in Review
- Respond to comments and make updates as needed
- Use `git commit --amend` or `git rebase -i` for a clean commit history
- Push updates to the same branch to trigger CI reruns

Once your PR is merged:
- Sync your local main
- Delete the feature branch:

```bash
git checkout main
git pull origin main
git branch -d feat/scheduler-prioritization
```

<!-- TOC --><a name="-support-questions"></a>
## 🙋 Support & Questions

- For bugs or issues, open issues in the right repository:
  - [GitHub issue - `kokaq-core`](https://github.com/kokaq/kokaq-core/issues)
  - [GitHub issue - `kokaq-protocol`](https://github.com/kokaq/kokaq-protocol/issues)
  - [GitHub issue - `kokaq-server`](https://github.com/kokaq/kokaq-server/issues)
  - [GitHub issue - `kokaq-client`](https://github.com/kokaq/kokaq-client/issues)
- For design questions or roadmap discussion, open a [GitHub discussion](https://github.com/orgs/kokaq/discussions)

## 🙌 Thank You!

Your contributions help make `kokaq` a fast, flexible, and developer-first queuing platform.

---

> Generate TOC with https://github.com/derlin/bitdowntoc
