<div align="center">
  <img height="300" src="../kokaqfull.png" alt="cute quokka as kokaq logo"/>
</div>

`kokaq` is a distributed, cloud-native priority queue implementation, designed to solve the long-standing gap of native priority handling in cloud messaging systems. It’s built for high availability, low latency, and intelligent resource allocation — empowering mission-critical workflows with dynamic, weight-based prioritization.

---

## 🚀 Key Features

- **Native Priority Queue Support**  
  Prioritize tasks and messages based on their true importance — no workarounds or consumer hacks required.

- **Non-Discrete Priorities**  
  Fine-grained control using continuous, weight-based priority values instead of fixed levels.

- **Cloud-Native Architecture**  
  Built from the ground up on kubernetes and other modern cloud environments, leveraging serverless and container-native workflows.

- **Low Latency & High Availability**  
  Designed to handle latency-sensitive and real-time workloads with minimal delay and strong reliability.

- **Strict Highest-Priority-First Model**  
  Ensures that the most important messages are always processed first, deterministically.

- **SLA-Aware Resource Efficiency**  
  Prevents resource waste by adjusting queue behavior based on time-bound message SLAs.

- **Observability and Insights**  
  Built-in support for real-time monitoring through open telemetry.

- **Service Integration Ready**  
  Seamlessly connects with Azure Functions, AWS Lambda, Cloud Functions

---

## 💡 Why `kokaq`?

Cloud native message queue services don’t support real priority queues. `kokaq` introduces first-class support for prioritization, non-discrete weights, SLA-driven scheduling, and high-performance task routing — all without relying on multiple queues or consumer juggling.

---

## 🎯 Project Goals

- Fully open-source, extensible, and modular
- Native Cloud integration with pluggable backend storage
- REST and gRPC APIs
- SDKs for .NET, Python, JavaScript (coming soon)
- Designed for real-time ops, workflows, ML inference, and automation

---

## 📦 Roadmap

- [ ] Queue Engine with Weighted Priority Model
- [ ] Strict Priority-Based Dequeueing Algorithms
- [ ] gRPC and REST APIs
- [ ] Metrics Exporters (OpenTelemetry / Prometheus)
- [ ] SLA-aware Scheduling Engine
- [ ] SDKs and CLI tools

---

## 🛠 Use Cases

- Real-time job processing with strict SLA guarantees
- Scheduling ML inference jobs by impact/urgency
- Event processing with dynamic business priority
- Smart prioritization in CI/CD or build pipelines
- Financial transaction routing or alerting

---

## 🤝 Join the Community

`kokaq` is designed by engineers for engineers. Your feedback, feature ideas, and contributions are welcome!

---

## 📜 License

MIT License
