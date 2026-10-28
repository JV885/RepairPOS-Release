# 🛠️ RepairPOS by JV — Official Public Releases

> **An offline-first Windows desktop Point-of-Sale (POS) and Electronics Repair Service management platform.**  
> *Re-engineered from the ground up on a high-performance, 60 FPS Flutter desktop engine.*

---

## 🚀 Current Production Release: `v3.0.0`
* **Release Date:** October 2026
* **Target OS:** Windows 10 / 11 (64-bit Native)
* **Architecture:** Flutter Material 3 / Impeller-Skia (Hardware-Accelerated 60 FPS on 4GB RAM)
* **Authoritative Manifest:** [manifest.json](manifest.json)

---

## 📥 Downloads & Installation

| Package | Type | Intended Audience | Direct Download |
| :--- | :--- | :--- | :--- |
| **RepairPOS_Setup.exe** | **Windows Setup Wizard** | **New Users** (First-time installation) | [🔗 **Download Setup Installer**](https://github.com/JV885/RepairPOS-Release/releases/download/v3.0.0/RepairPOS_Setup.exe) |
| **RepairPOS.exe** | **v3.0.0 Application Binary** | **Existing Users** & Standalone Portable | [⚡ **Download v3.0.0 Executable**](https://github.com/JV885/RepairPOS-Release/releases/download/v3.0.0/RepairPOS.exe) |

---

## 🧭 How to Install or Upgrade

### 👶 For New Users:
1. Download [**RepairPOS_Setup.exe**](https://github.com/JV885/RepairPOS-Release/releases/download/v1.5.1/RepairPOS_Setup.exe).
2. Run the installer and follow the on-screen steps.
3. Launch **RepairPOS by JV** from your Desktop or Start Menu.
4. On first boot, the in-app updater will automatically detect and upgrade your installation to the latest **3.0.0** Flutter engine!

### 🔄 For Existing Users (In-App Auto-Updater):
1. Simply launch your current RepairPOS application.
2. The app automatically checks [manifest.json](https://raw.githubusercontent.com/JV885/RepairPOS-Release/refs/heads/main/manifest.json).
3. When **3.0.0** is detected, click **"Download & Install Update"**.
4. The application cryptographically validates the SHA-256 checksum, performs an atomic upgrade with `.bak` rollback safety, and restarts without touching your local database (`shop.db`).

---

## ✨ Key Feature Highlights in v3.0.0

### 🏎️ 1. Ultra-Smooth Performance on 4GB RAM
* **Hardware-Accelerated 60 FPS:** Replaced software canvas emulation with GPU-rendered native controls.
* **Low Memory Usage:** Runs between **~55MB and 75MB of RAM**—leaving your system fast and responsive.
* **Zero Input Delay:** Virtualized lists (`ListView.builder`) allow instant scrolling across thousands of products and tickets without dropping a frame.

### 🔍 2. Real-Time Hardware & Service Knowledgebase
* **Instant In-Memory Search:** Search phone models (e.g., *Galaxy A12, Redmi 9A, Infinix Hot 10 Play*) on every keystroke in 0.05ms.
* **Hardware Cross-Compatibility:** Check compatible LCD assemblies and cross-compatible battery models.
* **Security Bypass Guide:** Quick reference for FRP and unlock methods by Android version (Test Point, USB Brom, EDL, ISP, Manual shortcuts).
* **Scrap Board Pricing Matrix:** Reference values for donor and scrap motherboards categorized by capacity and Code vs. Non-Code status.
* **Live CRUD & Cloud Sync:** Add, edit, and delete device specifications locally with immediate background sync to Cloudflare Workers.

### 🛒 3. Unified Retail POS & Repair Settlement
* **Atomic Settlement:** Sending a repair ticket to the POS cart links the repair directly into the retail transaction.
* **Proportional Discounting:** Applying cart discounts automatically adjusts repair revenue and technician commission splits fairly.
* **Zero Double-Counting:** Completely eliminates duplicate transactions in the ledger.

### 🧾 4. Thermal Paper Style Receipt Popup
* **Fitted Modal:** Designed like real 370px thermal receipt paper.
* **Instant Dismissal:** Closes instantly by pressing the **`ESC` key** or clicking outside the popup.
* **Configurable Legal Notice:** Features an editable **180-Day Unclaimed Device Policy Notice** and **Warranty Coverage Terms** managed directly from Settings.

### 📊 5. Financial Dashboard & Direct Vector PDF Export
* **No Missing-Glyph Tofu Boxes (`▯`):** Clean, universal currency rendering for Philippine Peso (`PHP`).
* **Direct-to-Disk PDF Export:** Bypasses buggy Windows print spoolers to write `.pdf` files directly to `app_data/reports/` and opens them automatically.
* **Daylight High-Contrast PNG Reports:** Crisp GPU-rendered image reports for single-day audits (capped at 20 items to prevent memory bloat).
* **Individual Transaction Deletion:** Delete specific ledger rows with automatic inventory stock return (`VOID_SALE`).

### 🛡️ 6. Cloudflare D1 Real-Time Sync & 180-Day Auto-Purge
* **Public Data Sanitization:** Internal parts costs, technician splits, and shop owner profit are stripped before pushing customer tracking updates to Cloudflare D1.
* **Automated Maintenance:** Closed or cancelled repair tickets older than **180 days** are automatically cleaned up on startup to keep your database fast and lightweight.

---

## 🔒 Security Architecture
* **Offline PBKDF2 Encryption:** Passwords are never stored in plain text. Offline authentication uses PBKDF2-HMAC-SHA256 with 100,000 iterations and per-user cryptographic salts.
* **Integrity Guard:** Every update package is checked against its unique SHA-256 hash before execution.
* **Database Immutability:** Updating the application binary **never touches, resets, or overwrites** your local SQLite database (`shop.db`).
