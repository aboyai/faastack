# FaaStack – Serverless Functions on OpenStack
**Effortless Serverless. OpenStack Powered.**

FaaStack is a blazing-fast serverless execution engine purpose-built for OpenStack environments. Deploy, scale, and monitor event-driven functions without managing servers. Inspired by AWS Lambda, optimized for private clouds.

---

## 🚀 Features

- **Serverless Function Execution**  
  Trigger functions via HTTP, events, or cron – with dynamic scaling.
  
- **OpenStack Native**  
  Uses Nova, Swift, Keystone, and Neutron for compute, storage, auth, and networking.

- **Multi-Language Support**  
  Run functions in Go, Python, Node.js, Java (via lightweight container runtimes).

- **Event-Driven Architecture**  
  Trigger from OpenStack services (e.g., Swift events), webhooks, queues.

- **Function Gateway (API Gateway)**  
  Route and manage function endpoints with custom domains and SSL.

- **Built-in Observability**  
  Logs, metrics, and traces for every function invocation.

- **Secure Multi-Tenant Isolation**  
  Namespace isolation per tenant with resource quotas.

---

## 📊 Architecture Overview

```
          ┌──────────────┌       ┌───────────────┌
 HTTP →  │ Function   │  →→→  │ Execution     │  →→→  OpenStack Nova VMs
 Events→ │ Gateway    │       │ Engine        │  →→→  or Containers (K8s/Nova)
          └──────────────┘       └──────────────┘
               │                      │
               ▼                      ▼
          Auth (Keystone)       Storage (Swift/Glance)
               │                      │
          Metrics + Logs        Networking (Neutron)
```

---

## ⚙️ Quickstart

### 1. Deploy FaaStack on OpenStack  
```bash
git clone https://github.com/yourorg/faastack.git
cd faastack
make deploy
```

### 2. Deploy a Function  
```bash
faastack deploy \
  --name hello-fn \
  --runtime python3.10 \
  --entry handler.py \
  --trigger http \
  --memory 128MB \
  --timeout 10s
```

### 3. Invoke via HTTP  
```bash
curl https://gateway.faastack.cloud/functions/hello-fn \
  -d '{"name": "World"}'
```

---

## 📁 Repository Structure

```bash
faastack/
├── cmd/                 # CLI tool
├── gateway/             # Function Gateway (Go, gRPC)
├── engine/              # Execution Engine (Go, OpenStack SDK)
├── runtimes/            # Prebuilt runtimes (Dockerfiles)
├── deploy/              # Terraform/Ansible scripts for OpenStack
├── docs/                # Developer and Operator documentation
└── README.md
```

---

## 📙 Documentation

- [Architecture Guide](docs/architecture.md)
- [CLI Usage](docs/cli.md)
- [Developer Guide](docs/dev-guide.md)
- [Security Model](docs/security.md)

---

## 💬 Community and Support

- Issues? → [GitHub Issues](https://github.com/aboyai/faastack/issues)
- Discussions → [GitHub Discussions](https://github.com/aboyai/faastack/discussions)
- Contribute → PRs welcome!

---

## 🛡 License

Apache 2.0 © 2025 FaaStack Authors

