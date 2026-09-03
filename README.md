# Umamusume Dark Mode Overlay 🌙

A lightweight, seamless dark mode overlay and audio companion for the PC/DMM client of **Umamusume: Pretty Derby** (`UmamusumePrettyDerby.exe`).

Matches the game window bounds in real time, applies an adjustable black tint without blocking mouse clicks, and provides a sleek floating control bar with game volume control, auto-mute on focus loss, and system tray integration.

---

## ✨ Features

- **🛡️ 100% Click-Through Overlay**
  - Uses native Win32 layered styles (`WS_EX_TRANSPARENT | WS_EX_LAYERED | WS_EX_NOACTIVATE`) so every mouse click, scroll, and drag passes straight through to the game.

- **🎛️ Floating Control Bar**
  - Compact, sleek pill bar anchored at the top-center of the game window.
  - **🌙 Opacity Slider (0% – 90%)**: Adjust screen darkness smoothly. Capped at 90% for window stability.
  - **🔊 Volume Slider (0% – 100%)**: Directly controls game volume via Windows Core Audio (WASAPI).

- **⚙️ Right-Click Expandable Menu**
  - **Right-click** anywhere on the control bar to toggle the options panel:
    - **Mute on focus loss**: Automatically mutes the game when you switch to another window or minimize the game, and restores audio when you return.
    - **Autostart with Windows**: Toggles a startup shortcut in Windows Startup (`shell:startup`). If you ever move the application to a new folder, it automatically revalidates and repairs the shortcut path on launch.

- **🔇 Intelligent Volume Preservation**
  - Never gets stuck at 0% when launching or loading the game.
  - Safely records the exact volume level *prior* to focus loss and saves it to configuration.
  - Always restores game audio on application close, game exit, or PC shutdown.

- **🔔 System Tray Integration**
  - **No Taskbar Clutter**: Runs silently in the background without occupying space on your Windows taskbar (`ShowInTaskbar="False"`).
  - **Instant Startup**: The tray icon appears immediately in the notification area upon Windows boot or app launch, even before the game is started.
  - **Left-Click**: Brings up or toggles the control bar.
  - **Right-Click**: Quick context menu with **Settings** and **Exit**.
  - **Explorer Crash Protection**: Automatically restores the tray icon if `explorer.exe` ever restarts.

- **⚡ Ultra-Low Resource Usage (Two-Loop Engine)**
  - **Idle Loop**: When the game is not running, checks for the process only once every 15 seconds (0% CPU impact).
  - **Active Loop**: When the game is running, tracks window position and size at ~60 fps with sub-millisecond responsiveness.

---

## 📥 How to Download & Use

### Option 1: Download the Executable (.exe)
1. Download the latest release from the **Releases** section (or copy the compiled `UmamusumeDarkMode.exe`).
2. Move `UmamusumeDarkMode.exe` to a permanent folder of your choice (e.g. `C:\Tools\UmamusumeDarkMode\` or `C:\Program Files\UmamusumeDarkMode\`).
3. Run `UmamusumeDarkMode.exe`.
   - The app icon will immediately appear in your **Windows System Tray** (near the clock in the bottom-right corner).
   - *(Optional)* Right-click the control bar (or the tray icon) and check **Autostart with Windows** so it starts automatically with your PC.

### Option 2: Running with Umamusume
- You can start `UmamusumeDarkMode.exe` **before or after** launching Umamusume.
- As soon as the game opens, the dark overlay and top control bar will snap onto the game window automatically.
- When you minimize or switch away from the game, the overlay hides (and audio mutes if enabled) until you click back into the game.

---

## 🎮 How to Control

| Action | How to do it |
| :--- | :--- |
| **Adjust Darkness** | Drag the **🌙 Moon Slider** (defaults to 40%). |
| **Adjust Game Volume** | Drag the **🔊 Speaker Slider**. |
| **Open Settings Menu** | **Right-click** anywhere on the control bar. |
| **Toggle Mute on Focus Loss** | Click **Mute on focus loss** in the expanded menu. |
| **Toggle Windows Startup** | Click **Autostart with Windows** in the expanded menu. |
| **Tray Quick Menu** | **Right-click** the tray icon for **Settings** or **Exit**. |

---

## ⚙️ Configuration & Settings

Settings are automatically stored in JSON format at:
```text
%LocalAppData%\UmamusumeDarkMode\settings.json
```
This stores your preferred opacity, volume level, and focus-mute preference across sessions.

---

## 🛠️ Building from Source

### Prerequisites
- Windows 10 / 11
- [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)

### Build Command
Clone the repository and build:
```powershell
git clone https://github.com/your-username/UmamusumeDarkMode.git
cd UmamusumeDarkMode
dotnet build -c Release
```

### Publish as a Single Executable
To produce a self-contained, single-file `.exe`:
```powershell
dotnet publish UmamusumeDarkMode\UmamusumeDarkMode.csproj -c Release -r win-x64 --self-contained false -p:PublishSingleFile=true
```
The output executable will be generated at:
```text
UmamusumeDarkMode\bin\Release\net8.0-windows\win-x64\publish\UmamusumeDarkMode.exe
```

---

## 📄 License
MIT License. Feel free to use and modify for personal use.
