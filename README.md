<p align="center">
  <img src="logo.png" alt="BODY SPARK Logo" width="180" style="border-radius: 50%; box-shadow: 0 8px 24px rgba(0,0,0,0.15);" />
</p>

<h1 align="center">BODY SPARK</h1>
<h3 align="center">Enterprise Gym Management & Biometric Attendance System</h3>

<p align="center">
  <em>An autonomous workstation application engineered for commercial gyms and fitness clubs, featuring real-time ZKTeco biometric fingerprint integration, automated fee enforcement, financial loss/profit analytics, and cloud synchronization.</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011-0078D6?logo=windows&logoColor=white" alt="Platform" />
  <img src="https://img.shields.io/badge/Hardware-ZKTeco%20K50%20Biometric-00C853?logo=fingerprint&logoColor=white" alt="ZKTeco K50" />
  <img src="https://img.shields.io/badge/Frontend-React%2019%20%7C%20Vite-61DAFB?logo=react&logoColor=black" alt="React 19" />
  <img src="https://img.shields.io/badge/Backend-Node.js%20%7C%20SQLite%20WAL-339933?logo=nodedotjs&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/Security-Google%20Authenticator%202FA-EA4335?logo=google&logoColor=white" alt="2FA Security" />
  <img src="https://img.shields.io/badge/Cloud-Google%20Drive%20Sync-4285F4?logo=googledrive&logoColor=white" alt="Google Drive" />
</p>

---

## 📌 Project Overview

**BODY SPARK** is a high-performance gym management desktop software developed to solve daily front-desk challenges in gym operations. Unlike standard web-based portals that suffer from internet outages and slow responsiveness, BODY SPARK runs entirely offline on local hardware with direct TCP/IP socket connections to biometric hardware, while automatically pushing scheduled weekly snapshots to Google Drive for cloud redundancy.

### 🌟 Key Capabilities at a Glance
- ⚡ **Zero-Latency Biometric Verification**: Direct TCP/IP socket integration with **ZKTeco K50** machines.
- 🔔 **Auditory Verification Feedback**: Instant pleasant two-tone chimes for active members vs high-decibel warning buzzers for overdue/unpaid attempts.
- 👥 **Comprehensive Member Lifecycle**: Dynamic shift categorization (Morning, Evening, Night), membership duration plans, and real-time status transitions.
- 📊 **Financial Accounting & P&L Engine**: Monthly revenue calculation, categorized gym operational expenses (Rent, Electricity, Salaries, Equipment, Maintenance), and net profitability breakdown.
- ☁️ **Weekly Google Drive Synchronization**: Autonomous weekly background backup push and 1-click database restore for effortless new laptop provisioning.
- 🛡️ **Enterprise Security (2FA)**: Single-executable workstation installer protected by **Google Authenticator (RFC 6238 TOTP)**.

---

## 🏛️ System Architecture

```
┌────────────────────────────────────────────────────────────────────────┐
│                          BODY SPARK WORKSTATION                        │
├───────────────────────────┬────────────────────────────────────────────┤
│   React 19 Desktop Client │   High-Performance Local Backend           │
│   • Dark & Light Modes    │   • Node.js Event Loop Architecture        │
│   • Instant Search & Filter│  • SQLite Engine with WAL Journaling      │
│   • Monthly Accounts P&L  │   • Biometric TCP Session Supervisor       │
│   • Google Drive Portal   │   • Native Desktop Window Shell (C# .NET)  │
└─────────────┬─────────────┴─────────────────────┬──────────────────────┘
              │                                   │
              ▼                                   ▼
┌───────────────────────────┐       ┌────────────────────────────────────┐
│   ZKTeco K50 Biometric    │       │    Google Drive Cloud Storage      │
│   • Live Fingerprint Scans│       │    • Automated Weekly Snapshots    │
│   • Direct Ethernet/LAN   │       │    • 1-Click .bsbak File Restore   │
│   • Voice & Sound Alarms  │       │    • Safe Multi-Device Migration   │
└───────────────────────────┘       └────────────────────────────────────┘
```

---

## 🚀 Core Features

### 1. 🖲️ Biometric Hardware Integration (ZKTeco K50)
- **High-Speed Socket Engine**: Direct Ethernet connection supporting both direct PC-to-machine cables (`192.168.1.201`) and local Wi-Fi router LAN (`192.168.0.151`).
- **Real-Time Attendance Ingestion**: Captures timestamped check-in logs in sub-second time.
- **Custom Sound Effects**:
  - *Paid Chime*: Pleasant synthesized C5-G5 chime confirming authorized entry.
  - *Unpaid Alert*: Immediate high-frequency security buzzer alerting front-desk staff of expired accounts.

### 2. 👥 Gym Operations & Member Tracking
- Member records tracking gender, training shifts (Morning, Evening, Night), and membership tiers (Monthly, 3 Months, 6 Months, Yearly).
- Automated expiration engine that continuously recalculates due dates and updates membership flags.
- Biometric registration status indicator confirming enrolled fingerprints on the hardware.

### 3. 💳 Accounts, Expenses & Financial Engine
- **Gross Revenue Tracking**: Automatic receipt creation upon member payments.
- **Gym Expense Management**: Categorized overhead tracking including:
  - 🏢 Facility Rent
  - ⚡ Electricity & Utilities
  - 🏋️ Equipment & Maintenance
  - 👥 Staff & Trainer Salaries
  - 💊 Supplements & Inventory
  - 📢 Marketing & Operations
- **Monthly Filter Breakdown**: Select any calendar month to view instant totals:
  $$\text{Net Profit} = \text{Gross Revenue} - \text{Total Expenses}$$

### 4. ☁️ Google Drive Cloud Backup & 1-Click Laptop Migration
- **Weekly Autonomous Sync**: Body Spark takes a transaction-consistent SQLite snapshot and pushes it to a secure `Body Spark Backups` folder in Google Drive.
- **1-Minute Google Apps Script Webhook**: Requires zero third-party software or expiring API tokens.
- **New Laptop Provisioning**: Install on a new workstation, select the downloaded `.bsbak` backup file, and restore all members, fingerprints, financial receipts, and attendance logs in 1 click.
- **Automatic Rollback Guard**: Preserves a local safety copy before applying any database restore.

### 5. 🔒 Enterprise Security & Two-Factor Authentication
- **Installer Guarded by Google Authenticator**: The standalone setup file requires a live 6-digit TOTP code from the gym owner's smartphone app before unpacking.
- **Admin Session Locks**: Critical operations (editing member records, waiving fees, deleting entries) require administrative authorization.
- **Clean Slate Distribution**: Packaged installer automatically initializes a sanitized environment on new machines without residual test logs.

---

## 🛠️ Technology Stack

| Layer | Technology | Description |
| :--- | :--- | :--- |
| **Frontend UI** | React 19, Vite | Responsive single-page application with custom CSS design tokens |
| **Backend Core** | Node.js, Express | Event-driven backend with Server-Sent Events (SSE) live updates |
| **Database** | SQLite 3 (WAL Mode) | High-concurrency local database with checkpointing and ACID safety |
| **Biometric Protocol** | Node ZK-Lib (TCP/IP) | Low-level binary socket protocol for ZKTeco devices |
| **Desktop Shell** | C# .NET Windows Forms | Dedicated borderless window frame with System Tray minimization |
| **Cloud Sync** | Google Apps Script Webhook | Serverless Google Drive bridge with Base64 octet streams |
| **Security** | RFC 6238 TOTP (SHA-1) | Military-grade dynamic 2FA authentication algorithm |

---

## 👤 Author & Developer

**Hammad Shaikh**
- **GitHub**: [@Hammadshaikh1994](https://github.com/Hammadshaikh1994)
- **Email**: [hammadshk1994@gmail.com](mailto:hammadshk1994@gmail.com)
- **Role**: Full-Stack Software Engineer & Desktop Systems Architect

> *Available for custom enterprise software development, hardware/IoT biometric integrations, and tailored management solutions.*

---

## 📄 License & Proprietary Notice

Copyright © 2026 **Hammad Shaikh**. All rights reserved.

*Notice: This repository serves as a public architectural showcase and technical portfolio. Core proprietary backend algorithms, biometric firmware communication drivers, and commercial database binaries are maintained in private development repositories.*
