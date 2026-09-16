# RepairPOS by JV — Official Public Releases

Welcome to the official public distribution and update repository for **RepairPOS by JV** — an offline-first Windows desktop Point-of-Sale (POS) and Electronics Repair Service management platform.

---

## 🚀 Latest Version: `v1.5.2`
* **Released:** September 17, 2026
* **SHA-256 Checksum (`RepairPOS.exe`):** `c3be41790694457db8fe642a2e9f8307d603848c8691ad5008d686eda236b88d`

---

## 📥 Downloads

| File | Type | Target Audience | Download Link |
| :--- | :--- | :--- | :--- |
| **`RepairPOS_Setup.exe`** | Setup Installer | **New Users** (First-time installation) | [Download Setup Installer](https://github.com/JV885/RepairPOS-Release/releases/download/v1.5.2/RepairPOS_Setup.exe) |
| **`RepairPOS.exe`** | Application Binary | **In-App Auto-Updater** & Existing Users | [Download Executable](https://github.com/JV885/RepairPOS-Release/releases/download/v1.5.2/RepairPOS.exe) |

---

## 🔄 Automatic In-App Updates
If you already have RepairPOS installed on your computer, you do **not** need to manually download installers:
1. Launch the RepairPOS desktop application.
2. The application checks `https://github.com/JV885/RepairPOS-Release/raw/refs/heads/main/manifest.json`.
3. When `v1.5.2` is detected, click **"Download & Install Update"**.
4. The application automatically verifies SHA-256 checksums, updates itself, and restarts while preserving your local database.

---

## 🛡️ Security & Integrity
All update packages are verified using cryptographic SHA-256 hashing. The current release manifest is maintained in [`manifest.json`](manifest.json).
