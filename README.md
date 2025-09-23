<p align="center">
  <img src="https://raw.githubusercontent.com/PowerShell/PowerShell/master/assets/ps_black_64.svg" width="90" alt="PowerShell Logo"/>
</p>

# 🛠️ PowerShell Playbook

A modern, modular **PowerShell automation toolkit** for Windows and hybrid environments.
Designed to accelerate **IT operations, reporting, and troubleshooting** with reproducible scripts and HTML/CSV outputs.

---

## ✨ Features

- **Inventory & Reporting**
  - `Get-ServerRoleFeatureInventory` → Collects Windows Server role/feature inventory with CSV + HTML output
  - `Get-LocalAdminReport` → Audits local administrators on servers/workstations
  - `Get-CertificateExpiry` → Scans certificates nearing expiration
  - `Get-ConditionalAccessReport` → Pulls Conditional Access insights

- **Troubleshooting**
  - `Collect-SupportBundle` → Gathers logs, services, hotfixes, event logs, and network info into a zip + HTML summary
  - `Get-DefenderStatus` → Quick check of Windows Defender status

- **Automation Helpers**
  - `Invoke-WithRetry` → Retry logic wrapper
  - `Invoke-WinGetBaseline` / `Invoke-IntuneBaseline` → Baseline configuration via WinGet / Intune
  - `Write-ToolkitLog` → Consistent structured logging

- **Identity & Governance**
  - `Send-PasswordExpiryNotification` → Generate user password expiry reports & notifications
  - `Test-AdOnline`, `Test-Rbac` → Health checks and access testing

---

## 📂 Repo Structure

```
PowerShell-Automation-Toolkit/
├── src/                          # Core module code
│   ├── PowerShellPlaybook.psd1   # Module manifest
│   ├── PowerShellPlaybook.psm1   # Module entrypoint
│   ├── Public/                   # Exported functions
│   └── Private/                  # Internal helpers
├── tests/                        # Pester tests (Reports, Identity, WindowsOnly)
├── reports/                      # Generated reports (gitignored)
├── Run-Tests.ps1                 # Lint + Test runner (Pester 5, ScriptAnalyzer)
└── Diagnose-Playbook.ps1         # Self-check diagnostics
```

---

## 🚀 Getting Started

```powershell
# Clone the repo
git clone https://github.com/dj-3dub/PowerShell-Automation-Toolkit.git
cd PowerShell-Automation-Toolkit

# Import the module
Import-Module ./src/PowerShellPlaybook.psd1 -Force

# List available commands
Get-Command -Module PowerShellPlaybook
```

---

## 🧪 Testing & Linting

We ship with **Pester 5** + **PSScriptAnalyzer** support:

```powershell
# Run lint + tests
.\Run-Tests.ps1 -Output Detailed

# Optional: generate NUnit XML
.\Run-Tests.ps1 -Output Detailed -NUnitXml .	est-results.xml
```

CI/CD workflow coming soon (GitHub Actions).

---

## 📊 Sample Report

`Get-ServerRoleFeatureInventory -OutputPath ./reports`

<p align="center">
  <img src="docs/images/sample-report.png" width="700" alt="Server Role Inventory Report"/>
</p>

---

## 🧩 Requirements

- Windows PowerShell 5.1 **or** PowerShell 7+
- Windows Server for role/feature inventory
- Admin rights for some functions (Defender, SupportBundle)

---

## 📌 Topics
`powershell` · `automation` · `windows` · `enterprise` · `sysadmin` · `scripting` · `toolkit`

---

## 📜 License

MIT — free to use, modify, and share.
Contributions and improvements welcome!

---

## 🙌 Credits

Built with ❤️ by [Tim Hevein](https://github.com/dj-3dub).
Thanks to the PowerShell community for modules, best practices, and inspiration.
