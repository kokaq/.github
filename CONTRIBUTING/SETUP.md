## 🔧 Development Setup

  + [🧰 Prerequisites for Development Setup](#-prerequisites-for-development-setup)
  + [🚀 Getting Started](#-getting-started)
    - [1. Clone all repositories into the same folder:](#1-clone-all-repositories-into-the-same-folder)
    - [2. Initialize `go.work`](#2-initialize-gowork)
  + [Debug Mode (Default Dev)](#debug-mode-default-dev)
  + [Release Mode (CI / Production)](#release-mode-ci-production)



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
| Docker Desktop | Latest stable | For Debugging |

> Optional: Install via [golangci-lint installation guide](https://golangci-lint.run/usage/install/)

**📦 Go Environment Setup**

These repos are part of a modular Go project containing multiple services and modules:
- `core` is the heart of `kokaq`. It provides the foundational logic and data structures for enabling true, weight-based prioritization across distributed systems.
- `protocol` contains the canonical tcp protocol definitions for kokaq server.
- `server` is the production server component of `kokaq`. It hosts APIs, integrates with backend storage, exposes metrics, and runs the scheduling/dispatch logic 
  - depends on `core`, `protocol`
- `client` provides official SDKs to interact with `kokaq` server via REST and gRPC.
  - depends on `core`, `protocol`

<!-- TOC --><a name="-getting-started"></a>
### 🚀 Getting Started

<!-- TOC --><a name="1-clone-all-repositories-into-the-same-folder"></a>
#### 1. Clone all repositories into the same folder:

```bash
mkdir kokaq && cd kokaq
git clone https://github.com/kokaq/core.git
git clone https://github.com/kokaq/protocol.git
git clone https://github.com/kokaq/server.git
git clone https://github.com/kokaq/client.git
```
<!-- TOC --><a name="2-initialize-gowork"></a>
#### 2. Initialize `go.work`

```bash
go work init ./core ./protocol
```

It will generate:
```go
// go.work
go 1.21

use (
    ./core
    ./protocol
    ./server
    ./client
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

> Generate TOC with https://github.com/derlin/bitdowntoc