## 🧩 Marzban + Nginx + Node

**Marzban + Nginx Reverse Proxy** in Docker 🐳

This repository provides a complete setup using **Docker Compose** to run [Marzban](https://github.com/Gozargah/Marzban) (an Xray management panel) with **Nginx reverse proxy** and **SSL certificate** support.

---

### ✨ Features

* 🔐 Nginx reverse proxy for managing VMess, VLESS, Trojan, and Shadowsocks traffic
* 📊 Marzban panel accessible via a public port (`8899`)
* 🌐 Xray protocol access only via reverse proxy (no raw port exposure)
* 📦 Persistent configuration to ensure data remains safe even after `docker compose down`
* 🔧 Compatible with servers without public IPs, optionally integrates with **Cloudflare Tunnel**

---

### 📁 Folder Structure

```
.
├── docker-compose.yml         # Main Docker Compose file
├── nginx.conf                 # Main Nginx configuration
├── xray.conf                  # Reverse proxy virtual host for all protocols
├── marzban/  
│   └── xray_config.json       # Xray configuration (VMess, VLESS, etc.)
```

---

## 🚀 Quick Start

Clone this repository and start the services:

```bash
git clone https://github.com/sh4dowByte/marzban-nginx.git
cd marzban-nginx
```

## ☁️ Using Cloudflare Tunnel

To run Marzban + Nginx + Cloudflare Tunnel (without exposing public ports):

```bash
docker compose up -d marzban nginx cloudflared
```

Ensure your `.env` file contains your Cloudflare Tunnel token:

```env
TUNNEL_TOKEN=your_cloudflare_token
```

---

## ☁️ Secure & Easy Access to Marzban via Cloudflare Tunnel

Want to access your **Marzban panel** securely without exposing ports? Use **Cloudflare Tunnel** with a subpath like:

### 🌐 Example:

![1750807168500](image/readme/1750807168500.png)

Access Marzban at:

```
https://YOUR_DOMAIN/dashboard
```

---

### ⚙️ Marzban Panel Settings Example:

| VMESS                                          | VLESS                                          | TROJAN                                         |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| ![1750776686305](image/readme/1750776686305.png) | ![1750776700384](image/readme/1750776700384.png) | ![1750776717274](image/readme/1750776717274.png) |

---

### ✨ Benefits:

* 🔒 **Secure**: No need to expose port 80/443 publicly
* ☁️ **Reliable**: Leverages Cloudflare’s infrastructure — perfect for servers without public IPs
* 🎯 **Custom Path**: Run the panel under a subpath like `/dashboard`
* 💡 **Cost-Effective**: No need for static IP or premium VPS

### ⚠️ Cons:

* 🕓  **Slight Latency Overhead** : Requests go through Cloudflare’s edge, adding a small delay compared to direct IP access
* 🔧  **Tunnel Dependency** : If the Cloudflare Tunnel fails, access to your panel is lost (unless you expose it directly too)
* 🔒  **Cloudflare Account Required** : You must have a Cloudflare account and configure a domain or use a token
* 🧪  **Debugging Complexity** : Troubleshooting reverse proxy or path issues can be more complex compared to direct hosting

---

Thanks to the open-source community for continuously strengthening the Xray and Marzban ecosystem! 💪🚀

---
