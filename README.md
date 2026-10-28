# 1. Prepare README Content
$readmeContent = @"
# RepairPOS by JV — Official Public Releases

Welcome to the official public distribution and update repository for **RepairPOS by JV** — an offline-first Windows desktop Point-of-Sale (POS) and Electronics Repair Service management platform rebuilt with a high-performance 60 FPS Flutter desktop engine.

---

## 🚀 Latest Version: ``v3.0.0``
* **Released:** $(Get-Date -Format 'MMMM dd, yyyy')
* **Engine:** Flutter Material 3 / Impeller-Skia (Hardware-Accelerated 60 FPS on 4GB RAM)
* **Manifest:** [`manifest.json`](manifest.json)

---

## 📥 Downloads

| File | Type | Target Audience | Download Link |
| :--- | :--- | :--- | :--- |
| **`RepairPOS_Setup.exe`** | Setup Installer | **New Users** (First-time installation) | [Download Setup Installer](https://github.com/JV885/RepairPOS-Release/releases/download/v3.0.0/RepairPOS_Setup.exe) |
| **`RepairPOS.exe`** | Standalone Executable | **In-App Auto-Updater** & Portable Users | [Download Executable](https://github.com/JV885/RepairPOS-Release/releases/download/v3.0.0/RepairPOS.exe) |

---

## 🔄 Automatic In-App Updates
If you already have RepairPOS installed on your computer, you do **not** need to manually download installers:
1. Launch the RepairPOS desktop application.
2. The application automatically checks ``https://raw.githubusercontent.com/JV885/RepairPOS-Release/refs/heads/main/manifest.json``.
3. When ``v3.0.0`` is detected, click **"Download & Install Update"**.
4. The application automatically verifies SHA-256 checksums, updates itself, and restarts while preserving your local database.

---

## ✨ Key Features in v3.0.0
* **60 FPS Virtualized POS Catalog:** Zero-lag scrolling and barcode scanning for thousands of inventory items.
* **Smartphone Hardware & Bypass Knowledgebase:** Real-time search for LCD assemblies, cross-compatible batteries, Android bypass methods, and scrap board pricing.
* **Unified POS & Repair Settlement:** Proportional discount distribution with zero double-counting.
* **Thermal Paper Receipt Popup:** Dismissible with ``ESC`` or outside click, featuring editable 180-day unclaimed device policy notices and warranty terms.
* **Cloudflare D1 Real-Time Sync:** Background synchronization to the online tracking portal with full public data sanitization.
* **Vector PDF & Daylight PNG Exports:** Direct-to-disk report generation without Windows print spooler errors.

---

## 🛡️ Security & Integrity
All update packages are verified using cryptographic SHA-256 hashing. The current release manifest is maintained in [`manifest.json`](manifest.json).
"@

# 2. Clone, commit, and push
$tempClone = Join-Path $env:TEMP "repairpos_readme_push"
Remove-Item -Recurse -Force -ErrorAction SilentlyContinue $tempClone

Write-Host "Cloning release repository..." -ForegroundColor Cyan
git clone --depth 1 https://github.com/JV885/RepairPOS-Release.git $tempClone

if ($LASTEXITCODE -eq 0) {
    Set-Content -Path (Join-Path $tempClone "README.md") -Value $readmeContent -Encoding UTF8
    Push-Location $tempClone
    git add README.md
    git commit -m "Update README.md to v3.0.0 with active download links"
    Write-Host "Pushing README.md to GitHub..." -ForegroundColor Cyan
    git push origin
    Pop-Location
    Remove-Item -Recurse -Force -ErrorAction SilentlyContinue $tempClone
    Write-Host "`n✓ SUCCESS: README.md has been updated and pushed live to GitHub!" -ForegroundColor Green
    Write-Host "URL: https://github.com/JV885/RepairPOS-Release" -ForegroundColor Yellow
} else {
    Write-Error "Failed to clone repository. Check your network or Git permissions."
}
