<p align="center">
  <img src="docs/logo.png" alt="TH Guard" width="220">
</p>

<h1 align="center">TH Guard</h1>

<p align="center">
  Virus, suspicious program and hidden crypto-miner scanner for Windows.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Windows-10%20%7C%2011-0078D6?logo=windows" alt="Windows">
  <img src="https://img.shields.io/badge/.NET-8-512BD4?logo=dotnet" alt=".NET 8">
  <img src="https://img.shields.io/badge/license-MIT-green" alt="MIT License">
</p>

<p align="center"><a href="LEIAME.md">🇧🇷 Leia em português</a></p>

---

> TH Guard **does not replace your antivirus**. It uses **Microsoft Defender** as the virus detection engine and adds its own checks for what antivirus software often misses: hidden miners, disguised processes, startup persistence and security settings changed by malware.

## ✨ Features

### 🔍 Scans
- **Smart scan** (~1 min): processes, miners, startup items, system settings and browser extensions
- Microsoft Defender **quick and full scans**, with live progress
- **Folder or file**: TH Guard analysis + Microsoft Defender + **VirusTotal** (optional, free API key)
- Every alert shows its **risk level** (high, medium, low), the reason, the file and a fix button
- One-click "Fix all high" and "Trust" to hide alerts you recognize

### ⛏️ Miner detection
- Known miner names (XMRig, NiceHash, PhoenixMiner, T-Rex, lolMiner, NBMiner and more)
- Command lines with mining pools, miner parameters and crypto wallets
- Connections to ports used by mining pools
- **High CPU or GPU usage with no visible window** for more than 30 seconds
- Real-time monitor that **alerts immediately** when a possible miner shows up, even from the tray
- Shows how long the PC has been idle (miners often speed up then)

### 🕵️ Suspicious processes
- Programs **named like Windows processes running from the wrong folder** (e.g. svchost.exe in AppData)
- **Lookalike names** (scvhost, svch0st...)
- **Double extensions** (invoice.pdf.exe)
- Missing or **tampered** digital signatures
- Running from temp, Downloads or Public folders
- PowerShell, mshta, rundll32 and certutil commands used to download or hide code

### 🚀 Startup (Autoruns style)
- Registry (Run/RunOnce), Startup folder, scheduled tasks (including hidden), services
- **WMI subscriptions**, program hijacking (IFEO), altered Winlogon and AppInit_DLLs
- Digital signature and risk for each entry
- **Disable with backup**, restorable from quarantine

### 🛡️ Security settings
- Antivirus and real-time protection, definition age, tamper protection
- **Defender exclusions** (malware adds exclusions to hide)
- **Hosts** file redirecting banks, Windows Update or antivirus sites
- **Proxy** hijacking, Firewall, UAC, SmartScreen and PUA blocking
- Fix button on each item

### 🗃️ Quarantine and history
- Isolated, scrambled files (can't run), with restore
- Disabled startup items can be restored too
- Microsoft Defender threat history

### 🎨 Customization
- Dark, black and light themes, accent colors and logo color

## 📥 Download

Get the latest version from [**Releases**](https://github.com/Thiagosystems/THGuard/releases).

> No installation needed: the .exe already includes .NET. Works on Windows 10/11 64-bit and asks for **administrator** permission.
> The interface is currently in Portuguese.

## 🛠️ Build

Requirement: [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)

```bat
git clone https://github.com/Thiagosystems/THGuard.git
cd THGuard
build.bat
```

The executable is created at `publish\THGuard.exe`.

## 📁 Structure

| File | Purpose |
|---|---|
| `Rules.cs` | Rules: miners, pools, Windows processes, suspicious commands |
| `ProcessScanner.cs` | Processes, CPU/GPU usage and risk evaluation |
| `StartupScanner.cs` | Everything that starts with Windows |
| `SystemChecks.cs` | Defender, exclusions, hosts, proxy, firewall, UAC, extensions |
| `Defender.cs` | Microsoft Defender, VirusTotal and folder scan |
| `Signatures.cs` | Digital signatures and hashes |
| `Quarantine.cs` | Quarantine and fixes |
| `MainWindow.xaml` | User interface |

## ⚠️ Notes

- Heuristics can produce **false positives**: an alert is a reason to take a closer look, not a certainty. Use "Trust" for programs you know.
- VirusTotal only receives the file's **hash**, never the file itself.
- Files in the Windows folder are never quarantined.

## 📄 License

Distributed under the MIT License. See [LICENSE](LICENSE).
