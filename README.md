<div align="center">

<img src="assets/aexyr-logo.png" alt="Æxyr Logo" width="120">

# Æxyr

**Autonomous AI Agent Platform**

*Deploy a fully autonomous AI agent with a single Docker command.*

![Docker](https://img.shields.io/badge/Docker-Multi--Arch-2496ED?logo=docker&logoColor=white)
![Platforms](https://img.shields.io/badge/Platforms-amd64_%7C_arm64-4A154B)
![License](https://img.shields.io/badge/License-Proprietary-orange)
![Version](https://img.shields.io/badge/Version-1.0.0-blue)
![Trial](https://img.shields.io/badge/Trial-10_Days_Free-brightgreen)

---

**[Storefront](https://aexyr-store.axonstellar.ai)** · **[EULA](EULA.md)** · **[Changelog](CHANGELOG.md)** · **[Third-Party Notices](THIRD-PARTY-NOTICES.md)**

</div>

---

## Overview

Æxyr is an autonomous AI agent that lives inside a Docker container. It operates its own Linux environment, manages services, writes and executes code, browses the web, and orchestrates multi-agent workflows — all through a real-time web interface.

Give it a task. It figures out how, executes the steps, verifies the results, and comes back with the answer. No hand-holding, no copy-pasting commands.

```bash
docker run -d --name aexyr -p 9594:80 ghcr.io/axonstellar/aexyr:latest
```

Open `http://localhost:9594` → Login with `admin` / `aexyr` → Add an API key in Settings → Start building.

---

## Screenshots

### Agent Chat — Dark Theme
The main interface. Converse with Æxyr, assign tasks, and watch it work in real time. Code execution, file creation, web browsing, and multi-agent delegation all happen inline.

![Agent Chat](screenshots/main_dark.png)

### Network Topology
Live visualization of your entire service constellation. Every running service, LLM provider, SSL certificate, and infrastructure component appears as an interactive node. Drag nodes to arrange your constellation — positions are saved persistently, letting you design a layout that reflects your architecture. Click any node to inspect its health, view configuration, or tail logs in real time. Connection lines trace data flow, API calls, and dependencies between services, giving you an at-a-glance understanding of how everything fits together.

![Topology](screenshots/topology_dark.png)

### Server Rack
Real-time service dashboard. Start, stop, and restart services. Monitor ports, health status, and resource allocation across your constellation.

![Server Rack](screenshots/rack_dark.png)

### System Vitals
CPU, memory, disk, and process monitoring with historical charts. Identify resource-hungry processes and track system health over time.

![Vitals](screenshots/vitals_dark.png)

### Neural Core
The Action Potential Protocol — Æxyr's decision-making engine visualized. Watch confidence, safety, and necessity signals fire in real time as the agent evaluates actions.

![Neural Core](screenshots/neural_dark.png)

### Operations Center
System-level operations dashboard. Network listeners, nginx proxy configuration, process management, and terminal access in one view.

![Ops Center](screenshots/opscenter_dark.png)

### SSL Certificate Management
Provision, assign, and monitor SSL certificates. Automatic nginx configuration, domain-to-service binding, and renewal tracking.

![Certificates](screenshots/certificates_dark.png)

### File Manager
Browse, edit, upload, and download files across the entire user space. Syntax-highlighted editor with support for all common file types.

![Files](screenshots/files_dark.png)

---

## Features

### Autonomous Agent
- **Multi-step task execution** — breaks down complex tasks, executes each step, verifies results
- **Code execution** — writes and runs Python, Node.js, and shell commands in a live Linux environment
- **Web browsing** — autonomous browser agent for research, data extraction, and interaction
- **Multi-agent orchestration** — spawns specialized sub-agents (developer, researcher, hacker profiles) for parallel work
- **Long-term memory** — FAISS vector database for persistent knowledge across conversations
- **File & project management** — creates, edits, and organizes files and full project structures

### 8 LLM Providers
| Provider | Models |
|---|---|
| OpenRouter | 200+ models (Claude, GPT, Gemini, Llama, Mistral, etc.) |
| Anthropic | Claude Opus, Sonnet, Haiku |
| OpenAI | GPT-4.1, GPT-4o, o1, o3 |
| Google | Gemini 2.5 Pro, Flash |
| Mistral | Mistral Large, Medium, Small |
| Groq | Ultra-fast inference (Llama, Mixtral) |
| xAI | Grok |
| Ollama | Run local models — fully offline, zero API cost |

Configure different models for chat, utility, and browser tasks independently.

### AxonStellar Platform
| Module | Purpose |
|---|---|
| **Server Rack** | Real-time service dashboard — start, stop, restart, monitor |
| **Topology** | Interactive constellation map with persistent node placement, live health, and connection tracing |
| **Manifests** | Persistent service registry with auto-discovery |
| **Vitals** | CPU, memory, disk monitoring with historical charts |
| **Ops Center** | Network, nginx, process management, terminal |
| **Neural Core** | Action Potential Protocol — decision-making visualization |
| **SSL Management** | Certificate provisioning, domain binding, auto-renewal |
| **Files** | Full file manager with syntax-highlighted editor |
| **Tasks** | Scheduled and ad-hoc autonomous task execution |
| **Engrams** | Pre-built workflow playbooks for common operations |
| **Notifications** | Platform-wide alerting system |
| **Page Builder** | Visual web service designer with deploy-to-production |

### Infrastructure
- **Nginx reverse proxy** with automatic SSL configuration
- **Cloudflare Tunnel** support for secure external access (no port forwarding)
- **Process Manager** for service lifecycle management
- **Multi-service deployment** — run databases, caches, APIs, and full-stack apps inside the container
- **Port allocation** — services on 9551-9580, microservices on derived 35xx ports

### Security
- **Container hardening** — `cap_drop: NET_RAW`, `no-new-privileges`, iptables egress rules
- **Authentication** — session-based login with configurable credentials
- **EULA enforcement** — mandatory acceptance gate before platform access
- **License signing** — cryptographically verified license keys
- **Source protection** — critical modules compiled with Cython

---

## Quick Start

### Prerequisites

- **Docker** 20.10+ installed
- **An API key** from at least one supported LLM provider

### Docker Run

```bash
docker run -d --name aexyr -p 9594:80 \
  -v aexyr-data:/aexyr/usr \
  -v aexyr-logs:/aexyr/logs \
  -v aexyr-tmp:/aexyr/tmp \
  -v aexyr-data2:/aexyr/data \
  ghcr.io/axonstellar/aexyr:latest
```

### Docker Compose

Create a `docker-compose.yml`:

```yaml
services:
  aexyr:
    container_name: aexyr-agent
    image: ghcr.io/axonstellar/aexyr:latest
    restart: unless-stopped
    ports:
      - "9594:80"
    volumes:
      - aexyr-data:/aexyr/usr
      - aexyr-logs:/aexyr/logs
      - aexyr-tmp:/aexyr/tmp
      - aexyr-data2:/aexyr/data
    environment:
      - AUTH_LOGIN=admin
      - AUTH_PASSWORD=aexyr
    mem_limit: 8g
    cpus: 4.0

volumes:
  aexyr-data:
  aexyr-logs:
  aexyr-tmp:
  aexyr-data2:
```

```bash
docker compose up -d
```

### ARM64 architecture

```bash
docker run -d --name aexyr -p 9594:80 \
  -v aexyr-data:/aexyr/usr \
  -v aexyr-logs:/aexyr/logs \
  -v aexyr-tmp:/aexyr/tmp \
  -v aexyr-data2:/aexyr/data \
  ghcr.io/axonstellar/aexyr:latest-arm64
```

Multi-arch manifests are available — `ghcr.io/axonstellar/aexyr:latest` auto-selects the correct architecture on most systems.

### First Login

1. Open `http://localhost:9594`
2. Login: `admin` / `aexyr`
3. Go to **Settings** → add your API key (OpenRouter, Anthropic, OpenAI, etc.)
4. Start chatting — Æxyr is ready to work

---

## Architecture

| Layer | Technology |
|---|---|
| **Backend** | Python (Flask + Socket.IO + Uvicorn) |
| **Frontend** | Alpine.js + Vanilla JS + HTML/CSS |
| **Proxy** | Nginx (reverse proxy, SSL termination) |
| **Memory** | FAISS vector database |
| **Process Management** | Supervisor + custom Process Manager |
| **Container** | Docker (Kali Linux base) |
| **Browser** | Playwright (Chromium) |

---

## Persistent Volumes

| Volume | Container Path | Purpose |
|---|---|---|
| `aexyr-data` | `/aexyr/usr` | User data, projects, chats, memory, settings |
| `aexyr-logs` | `/aexyr/logs` | Service and application logs |
| `aexyr-tmp` | `/aexyr/tmp` | Temporary files |
| `aexyr-data2` | `/aexyr/data` | Certificates and assignments |

All data persists across container restarts and upgrades.

---

## Pricing

| | Trial | Licensed |
|---|---|---|
| **Price** | Free | **$49.99** (one-time) |
| **Duration** | 10 days | Permanent |
| **Features** | Full platform access | Full platform access |
| **Binding** | — | One license per instance |
| **Activation** | Automatic | Online (once), then fully offline |

Purchase at **[aexyr-store.axonstellar.ai](https://aexyr-store.axonstellar.ai)**

---

## Environment Variables

| Variable | Default | Description |
|---|---|---|
| `AUTH_LOGIN` | `admin` | Web UI username |
| `AUTH_PASSWORD` | `aexyr` | Web UI password |
| `AEXYR_WEB_PORT` | `9594` | Host port mapping |
| `AEXYR_MEM_LIMIT` | `8g` | Container memory limit |
| `AEXYR_CPUS` | `4.0` | Container CPU limit |

API keys are configured through the Settings page after login — not via environment variables.

---

## Updates

```bash
docker compose pull && docker compose up -d
```

Or with `docker run`:

```bash
docker pull ghcr.io/axonstellar/aexyr:latest
docker stop aexyr && docker rm aexyr
# Re-run your docker run command
```

Persistent volumes ensure your data, projects, and settings survive updates.

---

## Support

- **Email:** contact@axonstellar.com
- **Issues:** [GitHub Issues](https://github.com/axonstellar/AEXYR/issues)

---

## License

Æxyr is proprietary software published by **AxonStellar LLC**.

Usage is governed by the [End User License Agreement (EULA)](EULA.md). A 10-day free trial is included with every installation. Continued use beyond the trial period requires a purchased license key.

See [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) for open-source component attributions.

---

<div align="center">

*Synaptic grid synced. All nodes online. Traffic is flowing.* 🚀

**[Get Started →](https://aexyr-store.axonstellar.ai)**

</div>