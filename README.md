# RepairPOS by JV

An offline-first Windows desktop Point-of-Sale (POS) and Electronics Repair Service management platform with integrated Cloudflare D1 real-time customer tracking and automated in-app updates.

## Architecture
- **Desktop Application**: Python 3 / CustomTkinter (`main.py`)
- **Local Database**: SQLite (`app_data/shop.db`)
- **Cloud Database**: Cloudflare D1 (`repairpos-production-d1`)
- **API Engine**: Cloudflare Worker (`repairpos-api`)
- **Customer Tracking Portal**: Cloudflare Pages (`web/frontend`)

## Building the Desktop Installer
1. Compile the application folder:
   ```powershell
   .\venv\Scripts\python.exe build_app.py