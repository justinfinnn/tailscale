# Tailscale Docker Setup

This repository provides a **Docker Compose** configuration for setting up **Tailscale**, a secure, zero-config VPN that allows private networking between devices.

## 📌 What is Tailscale?

[Tailscale](https://tailscale.com/) is a modern, WireGuard-based VPN that enables secure access to your devices from anywhere. It simplifies remote access without the need for port forwarding or complex firewall rules.

## 🛠 Services

### 🔗 Tailscale

- **Container Name:** `tailscale`
- **Image:** `tailscale/tailscale:latest`
- **Hostname:** `finncorp-server`
- **Network Mode:** `host` (Provides full network access)
- **Volumes:**
  - `./state:/var/lib/tailscale` → Stores authentication and state
- **Devices:**
  - `/dev/net/tun:/dev/net/tun` → Required for VPN tunnel functionality
- **Capabilities:**
  - `NET_ADMIN` → Allows network configuration changes
  - `NET_RAW` → Provides raw socket access for networking tasks
- **Environment Variables:**
  - `TS_AUTHKEY=[your authkey]` (Replace with your Tailscale authentication key)
  - `TS_STATE_DIR=/var/lib/tailscale` (Stores persistent state)
- **Restart Policy:** `unless-stopped` (Ensures the container runs continuously)

---

## 📌 Getting Started

### 1️⃣ Prerequisites

- Docker & Docker Compose installed ([Guide](https://docs.docker.com/get-docker/))
- A [Tailscale account](https://tailscale.com)
- **Tailscale authentication key**
  - Obtain an auth key from the [Tailscale Admin Panel](https://login.tailscale.com/admin/settings/keys)

### 2️⃣ Clone the Repository

```sh
git clone https://github.com/justinfinnn/tailscale.git
cd tailscale
```
