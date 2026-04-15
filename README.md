# 📱 OpenClaw Android AI Station

> A portable, low-cost AI workstation powered by a Samsung phone, running a full Linux environment and AI agent engine via Termux.

This project combines a **Samsung DeX-powered mobile desktop**, a **Termux-based Linux environment**, and the **OpenClaw AI agent framework** to create a fully functional, remotely accessible AI automation system.

It turns an old phone into a **self-hosted AI engine** capable of executing real-world tasks like messaging, scheduling, and automation.

---

## 🚀 Overview

This setup uses:

* A Samsung S-series phone as the core hardware
* Samsung DeX for a desktop-like experience
* Termux to run a Linux environment
* SSH to connect from a PC
* OpenClaw API to power an AI agent

The result is a **portable AI server** that you can control locally or remotely.

---

## 🧠 Architecture

```
[ Windows PC ]
      │
      │  SSH (PowerShell)
      ▼
[ Samsung Phone (DeX Mode) ]
      │
      ▼
[ Termux ]
      │
      ▼
[ Ubuntu (proot-distro) ]
      │
      ▼
[ OpenClaw AI Engine ]
      │
      ▼
[ External Actions (Messages, Calendar, Automation) ]
```

---

## 🧰 Tech Stack

* Samsung DeX (desktop environment)
* Termux (Linux compatibility layer)
* Ubuntu (via proot-distro)
* SSH (remote access)
* Node.js (runtime)
* OpenClaw (AI agent framework)
* Anthropic API (Claude models)

---

## 🛠 Prerequisites

* **Android Device:** Samsung S-series recommended (8GB+ RAM ideal)
* **Monitor + peripherals** (for DeX)
* **Termux:** Install via F-Droid (Play Store version is outdated)
* **Anthropic API Key:** https://console.anthropic.com/

---

## 📥 Installation Guide

### 1. Setup Termux & Linux Environment

```bash
pkg update && pkg upgrade -y
pkg install proot-distro openssh -y
proot-distro install ubuntu
proot-distro login ubuntu
```

---

### 2. Install Dependencies (Inside Ubuntu)

```bash
# Install Node.js 20
curl -fsSL https://deb.nodesource.com/setup_20.x | bash -
apt update && apt install -y nodejs git nano htop

# Clone OpenClaw
git clone https://github.com/v-zhivkov/OpenClaw.git
cd OpenClaw
npm install
```

---

### 3. Configure API Key

```bash
nano .env
```

Add:

```
ANTHROPIC_API_KEY=your_api_key_here
```

Save with:

* `CTRL + O` → Enter
* `CTRL + X`

---

## 🚀 The "One-Word" Workflow (Aliases)

Edit your bash config:

```bash
nano ~/.bashrc
```

Add:

```bash
# Start AI Engine (with Android network fix)
alias engine='cd ~/OpenClaw && OPENCLAW_DISCOVERY_BACKEND=dummy ./openclaw.mjs gateway --force'

# Launch Chat UI
alias chat='cd ~/OpenClaw && ./openclaw.mjs tui'

# System Monitor
alias monitor='htop'
```

Apply changes:

```bash
source ~/.bashrc
```

---

## 🏃 Running the AI System

### Local (on Phone)

**Terminal 1:**

```bash
engine
```

**Terminal 2:**

```bash
chat
```

---

### Remote Access (PC → Phone)

**On Phone (Termux):**

```bash
sshd
```

**On PC (PowerShell):**

```powershell
ssh <user>@<phone_ip> -p 8022
proot-distro login ubuntu
```

Then run:

```bash
engine
# then
chat
```

---

## 🤖 Features

* AI-powered command execution
* Chat-based interface (TUI)
* Remote control via SSH
* Persistent agent running on mobile hardware

---
* **OpenClaw – Core Capabilities (No Plugins)**

* Run terminal commands and scripts

* Execute Python code

* Create, edit, and refactor code

* Read, write, and manage files and folders

* Generate and modify documents

* Search the web and fetch page data

* Control a browser (navigate, click, screenshot)

* Break tasks into steps and complete them autonomously

* Run multi-step workflows

* Spawn and manage sub-agents

* Schedule and run automated jobs

* Execute background processes

* Send messages and return structured outputs

* Interact with user interfaces and display results

* Generate images, audio, and other media

---

## 🔧 Troubleshooting & Tips

### ⚠️ "System Error 13" Fix

Android blocks certain local network discovery features.

This project solves it using:

```bash
OPENCLAW_DISCOVERY_BACKEND=dummy
```

This is **required** for the engine and chat interface to communicate properly.

---

### 🧠 Memory Management

* Use:

  ```bash
  monitor
  ```
* Claude models are resource-heavy
* Restart engine if performance drops

---

### 🔑 API Errors

* **401 / 403 errors** = likely no credits
* Check: https://console.anthropic.com/

---

## 💡 Why This Project Matters

* ♻️ Reuses old hardware
* 💸 Avoids expensive cloud setups
* 🧳 Fully portable AI workstation
* 🔓 Highly customizable Linux environment
* 🤖 Brings AI agents closer to personal devices

---

## 🔮 Future Improvements

* Web-based interface
* Better automation integrations (APIs, webhooks)
* Persistent background services
* Enhanced security (auth layers, encryption)
* Multi-agent workflows

---

## 📝 License

This repository is a configuration and setup guide.

* OpenClaw belongs to its original authors: https://github.com/v-zhivkov/OpenClaw
* This guide is open for personal and educational use

---

## 🙌 Acknowledgements

* Termux community
* Samsung DeX ecosystem
* OpenClaw contributors
* Anthropic (Claude API)

---

## ⚡ Final Notes

This is not just a project — it’s a proof-of-concept that **powerful AI systems don’t need expensive infrastructure**.

A phone, a bit of Linux, and some creativity can go a long way.
