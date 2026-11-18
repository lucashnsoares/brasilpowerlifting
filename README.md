[🇺🇸 English](README.md) | [🇧🇷 Português](README.pt-BR.md)

# Gestão de Torneios Brasil Powerlifting — Offline Powerlifting Meet Manager

An offline-first powerlifting competition management and real-time LAN scoreboard system built for meet directors, gyms, and university barbell clubs. Available in **English** and **Portuguese (PT-BR)**[cite: 3].

> **Want a ready-to-run Windows app without compiling?**  
> Get the signed, auto-updating Windows version on the **[Microsoft Store ($9.99 / Free Trial)](https://apps.microsoft.com/store/detail/9N79D1086G2W)**. For non commercial use exclusevely.

---

## Key Features

- **100% Offline-First:** Runs locally on SQLite with automatic backups—zero internet required during a meet[cite: 3].
- **Real-Time LAN Devices:** Connect referees' phones (`/arbitro`), audience big screens (`/display`), warm-up room TVs (`/aquecimento`), and weigh-in stations (`/pesagem`) over local Wi-Fi on port `3000`[cite: 3].
- **Self-Healing Windows Launcher:** Includes a native C# desktop panel (`PainelPowerlifting.cs`) that prevents Windows sleep/hibernation, auto-restarts Node.js on unexpected crashes, detects your LAN IP, and configures Windows Firewall with one click[cite: 3].
- **Bring Your Own Cloud (Optional):** Contains no hardcoded private cloud keys. Non-commercial clubs can optionally connect their own custom API and database in the Cloud Center (`/nuvem`)[cite: 3].

---

## Prerequisites

- **Node.js (x64, v20 or newer)** — [Download from nodejs.org](https://nodejs.org/)
- **Windows 10/11 (x64)** with .NET Framework 4.x (pre-installed on Windows) if compiling the desktop launcher[cite: 3, 4]
- **C++ Build Tools** (only if `better-sqlite3` needs to compile a native binary for your Node.js version)

---

## Building & Running from Source

### 1. Clone and Install Dependencies

```powershell
git clone [https://github.com/lucashnsoares/brasilpowerlifting.git](https://github.com/lucashnsoares/brasilpowerlifting.git)
cd brasilpowerlifting
npm install
```

### 2. Choose How to Run

#### Option A: Quick Start (Command Line — Windows, macOS, or Linux)
Run the server directly without compiling the Windows wrapper:

```bash
node server.js
```

Open `http://localhost:3000` in your browser[cite: 3].

#### Option B: Build the Full Windows Desktop App (`PainelPowerlifting.exe`)
Compiling the C# launcher gives you the desktop control panel, automatic Wi-Fi IP detection, sleep prevention, crash auto-recovery, and one-click Windows Firewall setup[cite: 3].

1. **Compile `PainelPowerlifting.cs` (x64)** using the built-in Windows .NET compiler[cite: 4]:

   ```powershell
   C:\Windows\Microsoft.NET\Framework64\v4.0.30319\csc.exe /target:winexe /platform:x64 /optimize+ /out:PainelPowerlifting.exe /win32icon:icone_power.ico PainelPowerlifting.cs
   ```

2. **Copy `node.exe` into the project root folder:**  
   `PainelPowerlifting.exe` looks for `node.exe` in the same directory as `server.js`[cite: 3]. Copy it from your Node.js installation:

   ```powershell
   Copy-Item (Get-Command node).Source .\node.exe
   ```

3. **Launch the application:**  
   Double-click `PainelPowerlifting.exe`. It starts the local server on port `3000` and automatically opens `http://localhost:3000`[cite: 3].

---

## Connecting Phones & Smart TVs (Wi-Fi / LAN)

1. Connect the host PC, referee phones, and Smart TVs to the same Wi-Fi network[cite: 3].
2. Click **Allow Firewall (Wi-Fi)** inside `PainelPowerlifting.exe` (grants inbound TCP access on port `3000`)[cite: 3].
   - *If running via Option A (CLI), allow inbound TCP port `3000` manually in Windows Defender Firewall.*[cite: 2, 3]
3. Open the LAN URLs shown in the launcher (e.g., `http://<YOUR-LAN-IP>:3000/arbitro` and `http://<YOUR-LAN-IP>:3000/display`)[cite: 3].

### Local Data & Backups
Database files and automatic backups are stored in:
`%LOCALAPPDATA%\BrasilPowerlifting`[cite: 2, 3]

---

## License (Source-Available — Noncommercial)

This project is licensed under the **[PolyForm Noncommercial License 1.0.0](LICENSE.md)**.

- **Permitted for free:** Personal use, amateur competitions, charity lift-offs, and university/non-profit powerlifting clubs—including local meets that charge entry fees solely to cover venue, equipment, and event costs.
- **Commercial license required:** For-profit event promoters, commercial organizations, and sanctioned federations you must purchase a license by contacting us at [brasilpowerlifting.com.br](https://brasilpowerlifting.com.br).