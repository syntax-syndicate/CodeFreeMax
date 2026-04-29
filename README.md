# CodeFreeMax

> 🎉 **v3.0.0 Official Release Now Available!**
>
> Our brand-new PaaS architecture has officially launched. Please pull the latest repository to redeploy. The default port has been changed to **8877**; this will not conflict with previous versions of the application, so you can deploy with confidence.

🚀 Transforms IDEs and services—such as Kiro, Antigravity, Warp, Orchids, and Grok—into API services compatible with OpenAI, Claude, and Augment Code formats. ## ✨ Features

### Multi-Channel Support

| Channel | Claude Protocol | OpenAI Protocol | Free Tier | AugmentCode | Notes |
|------|:-----------:|:-----------:|:----:|:-----------:|------|
| Kiro | ✅ | ✅ | ❌ | ✅ | ⭐ AugmentCode Recommended Channel |
| Antigravity | ✅ | ✅ | ❌ | ✅ | ⭐ AugmentCode Recommended Channel |
| Warp | ✅ | ✅ | ❌ | ❌ | |
| Orchids | ✅ | ✅ | ❌ | ❌ | ⚠️ Sales Suspended |
| ClaudeCode | ✅ | — | ❌ | ❌ | Supports Claude Protocol Only |
| Grok | — | ✅ | ✅ | ❌ | Pure OpenAI Protocol |

- API Endpoint Format: `http://localhost:8877/{channel}/v1` (e.g., `/kiro/v1`, `/antigravity/v1`)

### 💰 Pricing

| Channel | Price | Daily Call Limit |
|------|:----:|:----------:|
| Kiro | ¥200/month | 86,400 calls/day |
| Antigravity | ¥300/month | 86,400 calls/day |
| Warp | ¥200/month | 10,000 calls/day |
| ClaudeCode | ¥300/month | 86,400 calls/day |

### ⚡ QPS Add-on Packs

QPS add-ons can be applied to any channel to increase the daily call limit:

| Item | Price | Description |
|------|:----:|------|
| +1 QPS | ¥200/month | Increases daily call limit by 86,400 |

> 💡 **Example**: The Kiro channel has a base limit of 86,400 calls/day. With +1 QPS, the limit becomes 172,800 calls/day; with +2 QPS, it becomes 259,200 calls/day; and so on. ### Core Capabilities

- 🔄 **Multi-Protocol Support** — Simultaneously supports Claude `/v1/messages` and OpenAI `/v1/chat/completions`.
- 🧠 **Automatic Context Compression** — ClaudeCode automatically compresses multi-turn conversations, ensuring ultra-long sessions remain uninterrupted and free of lag.
- 🚀 **Augment Code Compatibility** — Seamlessly acts as a reverse proxy for Augment Code, designed for use with custom-modified plugins.
- 🌐 **Proxy Pool** — Supports HTTP/HTTPS/SOCKS5 protocols, allowing for independent proxy configuration per channel.
- 🔑 **Session Derivation** — Proxy addresses support the `%s` placeholder, which is automatically replaced with the account's Session ID to ensure IP isolation.
- ⚖️ **Load Balancing** — Randomly distributes requests across multiple accounts while automatically skipping accounts experiencing errors.
- 🧹 **Feature Sanitization** — The Antigravity channel features built-in feature sanitization, anti-ban measures, and telemetry handling to mitigate risk control issues.
- 🔁 **Automatic Retries** — Configurable retry attempts, delay intervals, and specific retry logic for CAPTCHA challenges.
- 📋 **Model Management** — Customize model lists, map model names, and manage model status (enable/disable) and sorting order.
- 💾 **Data Persistence** — Utilizes MySQL storage for easy data backup and migration.
- 🎨 **Management Interface** — Features a brand-new frontend interface for intuitive and user-friendly operation.

## Quick Start

### 1. Download Deployment Files

```bash
git clone https://github.com/ssmDo/CodeFreeMax.git
cd CodeFreeMax/
```

### 2. One-Click Deployment

```bash
chmod +x deploy.sh
./deploy.sh
```

Running `./deploy.sh` will automatically execute the following steps: Stop the old service → Pull the latest Docker image → Start the service.

### 3. Common Commands

```bash
# View logs
docker compose logs -f

# Stop service
docker compose down

# Check status
docker compose ps
```

## Configuration Guide

### .env File

```bash
# Docker Image Configuration
DOCKER_IMAGE=ssmdo/kiro2api:latest

# Service Port
PORT=8877
```

### config.yaml File

```yaml
server:
address: ":8877"  # Service listening address

database:
default:
type: "mysql"
link: "mysql:root:password@tcp(127.0.0.1:3306)/augment"  # Database connection string
```

## Directory Structure

```
deploy/
├── README.md           # Deployment instructions
├── deploy.sh           # One-click deployment script
├── docker-compose.yml  # Docker Compose configuration
├── config.yaml         # Application configuration file
├── .env.example        # Environment variables example
└── data/               # Data directory (automatically created)
```

## FAQ

### 1. Port Already in Use

Modify the `PORT` variable in the `.env` file:

```bash
PORT=8080
```

### 2. Updating to the Latest Version

Simply re-run the deployment script:

```bash
./deploy.sh
```

### 3. Viewing Runtime Logs

```bash
docker compose logs -f
```

### 4. Data Persistence

Data is stored in the MySQL database; please back up your database regularly.

## 🔌 Companion Use with Augment Code

This project can be used in conjunction with a modified version of the Augment-BYOK plugin to enable the use of custom API endpoints within Augment Code.

👉 **Tutorial**: [Feishu Document](https://tcn1dv9putrz.feishu.cn/wiki/NfNEwWkGuiWhNJkHFdRcfXrPnn1)
🔑 **Access Password**: `734&Q851`

## 🙏 Acknowledgments

- [Augment-BYOK](https://github.com/AnkRoot/Augment-BYOK) - This plugin is a modified version based on this project; thanks to the original author for their open-source contributions.

## License

MIT License
