# 📱 Linux-on-Phone AI Agent Engine

A lightweight, unconventional setup that turns an old Samsung phone into a Linux-powered AI automation hub — accessible remotely and capable of executing real-world tasks.

---

## 🚀 Overview

This project uses a Samsung S-series phone running Samsung DeX as a desktop environment, combined with Termux to host a Linux environment. A remote PC connects via SSH to develop and control an AI agent system that can interact with external services (messages, calendar, etc.).

The result: a portable, low-cost “AI engine” running entirely off a phone.

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
[ Linux Environment ]
      │
      ▼
[ AI Agent Engine (OpenClawd API) ]
      │
      ▼
[ External Actions (Messaging, Calendar, etc.) ]
```

---

## 🧰 Tech Stack

* Samsung DeX (desktop environment)
* Termux (package manager + Linux layer)
* Linux (running inside Termux)
* SSH (remote access from Windows PowerShell)
* OpenClawd API (AI agent integration)

---

## ⚙️ Setup Process

### 1. Hardware Setup

* Connect a Samsung S-series phone to a monitor
* Enable Samsung DeX for desktop experience

### 2. Install Termux

* Install Termux on the phone
* Update packages:

  ```bash
  pkg update && pkg upgrade
  ```

### 3. Install Linux Environment

* Use a Linux distro inside Termux (e.g., Ubuntu via proot)
* Set up basic development tools

### 4. Enable SSH Access

* Install and start an SSH server in Termux
* Connect from your PC using:

  ```powershell
  ssh user@phone_ip
  ```

### 5. Build the AI Engine

* Integrate OpenClawd API
* Create a chat interface for interacting with the agent
* Implement command execution logic

---

## 🤖 Features

* Remote AI-controlled environment
* Execute commands through natural language
* Automate tasks like:

  * Sending messages
  * Reading notifications/messages
  * Managing calendar events
* Persistent “agent” environment running on mobile hardware

---

## 💡 Why This Is Cool

* Reuses old hardware (eco-friendly ♻️)
* Fully portable AI server
* Cheap alternative to cloud-based agents
* Hackable and customizable Linux environment

---

## ⚠️ Notes

* Performance depends on the phone’s hardware
* Background execution limits may apply depending on Android version
* Requires network configuration for stable SSH access

---

## 🔮 Future Improvements

* Add a web-based UI for the agent
* Improve automation integrations (APIs, webhooks)
* Optimize resource usage
* Add security layers (authentication, encryption improvements)

---


## 🙌 Acknowledgements

* Termux community
* Samsung DeX ecosystem
* OpenClawd API
