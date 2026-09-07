# SimLauncher

**One-click launcher for your entire sim racing setup.**

SimLauncher starts your game, voice spotter, force feedback tuner, dashboard overlay, and any other companion app — in the correct order, waiting for each one to actually be ready before starting the next. Save different setups as presets, switch between them instantly, and even trigger a full launch with a keyboard shortcut, without opening the app at all.

No more opening five programs by hand before every session.

![SimLauncher screenshot](docs/screenshot.png)

---

## Features

- **Ordered launch sequences** — define exactly which apps start, in what order, with per-app arguments and working directories
- **Smart wait strategies** — move to the next app only once the previous one is actually ready: fixed delay, wait for the process to appear, wait for its window title, or both
- **Presets** — save different setups (e.g. "Endurance stack", "Quick practice") as one-click tiles, each showing that preset's game icon
- **Global hotkeys** — launch a preset instantly with a shortcut like `Ctrl+Alt+1`, even while SimLauncher is hidden in the tray
- **System tray integration** — minimize to tray, auto-minimize once a sequence finishes, optionally run at Windows startup
- **Kill All** — stop everything a session launched with one click
- **Live status** — see at a glance whether each launched app is still running
- **Drag-and-drop reordering** — rearrange your launch sequence visually
- **Steam-aware icons** — automatically resolves the real installed executable behind a `steam://` launch link to show its actual icon
- **Portable** — a single self-contained `.exe`, nothing to install, works on any Windows 10/11 64-bit machine

## Download

Grab the latest `SimLauncher.exe` from the [Releases](../../releases) page. It's a single portable file — no installer, no prerequisites. Just run it.

> **Note:** since the executable isn't code-signed, Windows SmartScreen may show an "unrecognized app" warning the first time you run it. Click **More info → Run anyway**. This is normal for unsigned indie software, not a sign of a problem.

## Building from source

**Requirements:** [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)

```powershell
git clone https://github.com/<your-username>/SimLauncher.git
cd SimLauncher/SimLauncher
dotnet publish SimLauncher.csproj -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true -o publish
```

The finished executable will be at `publish/SimLauncher.exe`. That single file is everything you need — copy it anywhere, no other files required.

## Quick start

1. Open SimLauncher and accept the one-time license agreement.
2. Click the **+** button to add your first app — point it at an `.exe`, or use a launch URI (Steam games use `steam://rungameid/<appid>`).
3. Set a **wait strategy** so SimLauncher knows when that app is ready before starting the next one.
4. Repeat for each app in your stack, then reorder them by dragging the `⋮⋮` handle if needed.
5. Hit **START**.
6. Once you're happy with a sequence, click **Save Profile** to turn it into a reusable preset tile.
7. Optionally, open **Settings** (⚙) to assign a global hotkey to that preset, enable minimize-to-tray, or set SimLauncher to run at Windows startup.

## Where your data lives

All profiles and settings are stored locally at:

```
%AppData%\SimLauncher\
```

- `*.json` — your saved profiles/presets
- `settings.json` — app settings (startup, tray, hotkeys)
- `session.log` — a rolling log of recent launch activity

Nothing is sent anywhere; everything stays on your machine.

## Support

If SimLauncher's useful to you, you can [buy me a coffee](https://ko-fi.com/gm82_). Totally optional — the app is free either way.

## License

Licensed under the [MIT License](LICENSE) — free to use, modify, and redistribute, including commercially, as long as the copyright notice is kept. The in-app End User License Agreement (shown on first run) separately covers your use of the built application, including the standard no-warranty/liability terms.
