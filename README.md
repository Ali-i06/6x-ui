<div align="center">

# 6X-UI

**An advanced, heavily improved fork of [3X-UI](https://github.com/MHSanaei/3x-ui)**

[![Version](https://img.shields.io/badge/version-3.0.2-blue.svg)](#)
[![Go Version](https://img.shields.io/badge/go-1.22+-00ADD8.svg)](#)
[![Node](https://img.shields.io/badge/node-22+-339933.svg)](#)
[![License](https://img.shields.io/badge/license-GPL%20V3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0.en.html)
[![Fork of](https://img.shields.io/badge/fork%20of-3x--ui-orange.svg)](https://github.com/MHSanaei/3x-ui)

A powerful, open-source web-based control panel for managing Xray-core — rebuilt from the ground up with a modern Vue 3 frontend, improved architecture, and significant enhancements over the original.

</div>

---

## What is 6X-UI?

6X-UI is a heavily improved fork of [3X-UI by MHSanaei](https://github.com/MHSanaei/3x-ui), designed for users who need a more capable, modern, and maintainable Xray-core management panel.

While staying true to the spirit of the original, 6X-UI introduces a completely rebuilt frontend using Vue 3 + Ant Design Vue 4 + Vite 8, along with backend improvements and new features.

---

## Improvements Over 3X-UI

- **Fully rebuilt frontend** using Vue 3 (Composition API), Ant Design Vue 4, and Vite 8
- **Cleaner codebase** with better separation of concerns and maintainability
- **Improved UI/UX** with a more modern and responsive interface
- **Better performance** due to optimized build pipeline with Vite
- **Multi-entry architecture** — each page is a separate Vite entry for faster loading
- **Enhanced i18n support** — improved internationalization structure
- **ESLint integration** for consistent code quality across the frontend
- **Active development** with ongoing improvements and bug fixes

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Go (CGO enabled) + Gin framework |
| Database | SQLite (via go-sqlite3) |
| Frontend | Vue 3 + Ant Design Vue 4 + Vite 8 |
| Proxy Core | Xray-core |
| Realtime | WebSocket |
| i18n | vue-i18n v11 |

---

## Features

- 🌐 Multi-protocol support via Xray-core (VLESS, VMess, Trojan, Shadowsocks, and more)
- 📊 Real-time traffic monitoring and statistics
- 👥 Multi-user client management with traffic limits and expiry dates
- 🔐 Two-factor authentication (2FA / TOTP)
- 🤖 Telegram bot integration for notifications and management
- 🌍 Multi-language support (English, Farsi, Arabic, Chinese, Spanish, Russian, and more)
- 📦 Subscription link generation (with Clash/JSON formats)
- 🖥️ Node management for multi-server setups
- 🔑 API with token-based authentication
- 🌙 Dark/Light theme support
- 📱 Fully responsive design

---

## Requirements

### Server
- Linux (Ubuntu 20.04+ recommended)
- 64-bit OS
- At least 512MB RAM

### Development (Windows/Linux/macOS)
- [Go](https://go.dev/dl/) >= 1.22
- [Node.js](https://nodejs.org/) >= 22 (npm >= 10)
- GCC (for CGO) — on Windows install via [MSYS2](https://www.msys2.org/)

---

## Quick Install (Server)

```bash
bash <(curl -Ls https://raw.githubusercontent.com/Ali-i06/6x-ui/main/install.sh)
```

---

## Development Setup

### 1. Clone the repository

```bash
git clone https://github.com/Ali-i06/6x-ui.git
cd 6x-ui
```

### 2. Install frontend dependencies

```bash
cd frontend
npm install
```

### 3. Run frontend in development mode (hot reload)

```bash
npm run dev
```

### 4. Build frontend

```bash
npm run build
```

### 5. Run backend

```bash
cd ..
go run .
```

The panel will be available at `http://localhost:2053`

> Default credentials: `admin` / `admin`

---

## Project Structure

```
6x-ui/
├── config/          # App configuration
├── database/        # Database models and migrations
├── frontend/        # Vue 3 frontend (Vite + Ant Design Vue)
│   └── src/
│       ├── api/         # Axios + WebSocket setup
│       ├── components/  # Shared components
│       ├── composables/ # Vue composables
│       ├── entries/     # Multi-page entry points
│       ├── i18n/        # Internationalization
│       ├── models/      # Data models (inbound/outbound/etc.)
│       └── pages/       # Page components
├── sub/             # Subscription service
├── web/             # HTTP controllers, services, middleware
├── xray/            # Xray-core integration
└── main.go          # App entrypoint
```

---

## Contributing

Contributions are welcome! Please feel free to open issues and pull requests.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/my-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/my-feature`)
5. Open a Pull Request

---

## Credits

- [MHSanaei/3x-ui](https://github.com/MHSanaei/3x-ui) — the original project this fork is based on
- [alireza0](https://github.com/alireza0/) — original X-UI author
- [Iran v2ray rules](https://github.com/chocolate4u/Iran-v2ray-rules) (GPL-3.0)
- [Russia v2ray rules](https://github.com/runetfreedom/russia-v2ray-rules-dat) (GPL-3.0)

---

## License

[GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.en.html)

> This project is intended for personal and educational use. Please do not use it for illegal purposes.
