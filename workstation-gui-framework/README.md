# Universal Workstation GUI Framework

This directory contains the documentation and architectural overview for a universal, offline-first graphical user interface (GUI) designed for manufacturing edge devices.

## Overview

The framework was built using **Python and PyQt/PySide**, focusing on a highly responsive, touch-friendly interface for operators on the factory floor. It is designed to be hardware-agnostic, easily deployable via an automated offline installer, and highly secure.

## Key Architectural Features

### 1. Offline-First & Resilient
Factory networks can experience intermittent drops. This GUI framework does not rely on a constant connection to a central server to function.
- **Local SQLite Database:** All transactions, operator logins, and inspection data are saved to a local, encrypted SQLite database.
- **Asynchronous Sync:** When network connectivity is restored, a background worker synchronizes the local data to the main server without interrupting the operator's workflow.

### 2. Automated Offline Deployment
Deploying software to edge devices with restricted internet access is challenging.
- **Zero-Dependency Installer:** The framework includes a robust `.bat` / PowerShell installer that bundles Python, virtual environments, and all dependencies in an `offline_packages` directory.
- **One-Click Setup:** The installer creates local environments, provisions the database schema, and drops shortcuts onto the desktop automatically.

### 3. Dynamic Visual Theming
To reduce operator fatigue and accommodate different lighting conditions on the factory floor, the UI supports dynamic theming.
- **QSS Styling:** Fully decoupled UI styling using Qt Style Sheets (QSS).
- **Visual Feedback:** Critical statuses (e.g., "Pass" vs "Fail") trigger full-screen color overlays and distinct audio cues, ensuring the operator receives immediate, unambiguous feedback.

### 4. Security & Access Control
Protecting the integrity of the manufacturing data is paramount.
- **Role-Based Access Control (RBAC):** Operators must authenticate before starting a work order. Certain features (like overriding a failed test or accessing calibration menus) are locked behind supervisor or engineering credentials.
- **Data Integrity:** The application monitors the health of the local database and automatically backs it up daily, ensuring that no traceability data is lost due to hardware failure.

## Application Structure (Abstracted)

```
workstation-gui/
├── ui/
│   ├── main_window.py       # Core layout and routing
│   ├── styles/              # QSS themes (dark/light)
│   └── components/          # Reusable widgets (numpads, status indicators)
├── core/
│   ├── auth.py              # Operator authentication logic
│   └── sync_worker.py       # Background thread for server synchronization
├── db/
│   ├── local_db.py          # SQLite interface
│   └── migrations/          # Schema versioning
└── scripts/
    └── offline_install.bat  # Automated deployment script
```
