<div align="center">
  <a href="https://kokaq.io" target="_blank">
    <img height="200" src="../kokaq-full.png" alt="cute quokka as kokaq logo"/>
  </a>
</div>

`kokaq` is a distributed, cloud-native priority queue implementation, designed to solve the long-standing gap of native priority handling in cloud messaging systems. It’s built for high availability, low latency, and intelligent resource allocation — empowering mission-critical workflows with dynamic, weight-based prioritization.

## Repositories

| Repository                  | Build Status | Go Reference |
|-----------------------------|--------------|--------------|
| `core` - Core data structures and algorithms for distributed scheduling, backend-agnostic priority queue engine | [![Tests](https://github.com/kokaq/core/actions/workflows/go.yml/badge.svg)](https://github.com/kokaq/core/actions/workflows/go.yml) | [![Go Reference](https://pkg.go.dev/badge/github.com/kokaq/core.svg)](https://pkg.go.dev/github.com/kokaq/core) |
| `protocol` - Protocol definitions (TCP/OpenAPI/AMQP) used across client & server | [![Tests](https://github.com/kokaq/protocol/actions/workflows/go.yml/badge.svg)](https://github.com/kokaq/protocol/actions/workflows/go.yml) | [![Go Reference](https://pkg.go.dev/badge/github.com/kokaq/protocol.svg)](https://pkg.go.dev/github.com/kokaq/protocol) |
| `client` - SDKs and language bindings for interacting with the kokaq server | [![Tests](https://github.com/kokaq/client/actions/workflows/go.yml/badge.svg)](https://github.com/kokaq/client/actions/workflows/go.yml) | [![Go Reference](https://pkg.go.dev/badge/github.com/kokaq/client.svg)](https://pkg.go.dev/github.com/kokaq/client) |
| `server` - Server-side host, APIs (REST/gRPC/TCP), orchestration, and integrations | [![Tests](https://github.com/kokaq/server/actions/workflows/go.yml/badge.svg)](https://github.com/kokaq/server/actions/workflows/go.yml) | [![Go Reference](https://pkg.go.dev/badge/github.com/kokaq/server.svg)](https://pkg.go.dev/github.com/kokaq/server) |
| `repl` - An interactive REPL for exploring and debugging [kokaq](https://github.com/kokaq) message queues via gRPC. | [![Tests](https://github.com/kokaq/repl/actions/workflows/go.yml/badge.svg)](https://github.com/kokaq/repl/actions/workflows/go.yml) | [![Go Reference](https://pkg.go.dev/badge/github.com/kokaq/repl.svg)](https://pkg.go.dev/github.com/kokaq/repl) |

## 🤝 Join the Community

`kokaq` is designed by engineers for engineers. Your [feedback](https://github.com/kokaq/.github/tree/main/CONTRIBUTING#-support--questions), [ideas](https://github.com/orgs/kokaq/discussions), and [contributions](https://github.com/kokaq/.github/tree/main/CONTRIBUTING#contributing-to-kokaq) are welcome!

---

## 📜 License

MIT License
