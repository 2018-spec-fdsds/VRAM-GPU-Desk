# VRAM GPU Desk 1.24

## New in 1.24 — 60-day activation period and offline device activation

**Protected-state path and control startup fixed.** Activation state now resolves through the canonical Windows machine-wide data folder, including scheduled-task launches with a minimal environment. This prevents a relative-path/permissions error from blocking native GPU control startup. Ownership, access-control and recovery checks remain enabled; this does not give exclusive control over other GPU utilities.

**60 days from the first supported launch on this computer.** The period starts when an activation-enabled edition first runs on the machine, not from older, unverified usage records. Its protected local anchor is retained through ordinary application updates and uninstall/reinstall. Updating alone does not restart the 60 days or stop reminders after expiry.

**Reminders without functional restrictions.** After the period, every feature remains available. A localized, nonmodal reminder appears at least once an hour while the application runs and is kept above ordinary Windows windows. The Activation checkbox becomes visible after the period. Opening or closing the activation dialog does not disable GPU control, cooling, monitoring or process actions.

**20-character offline request and response.** Open Activation, generate a device request and save the 20-character code as a UTF-8 TXT file. The owner uses a private generator to produce a matching 20-character response tied to that device identity. Enter the response in the application; a valid response stops the reminders. If the machine identity changes, a new response may be required; the original trial period is not restarted.

**Local state and a private issuer.** The request is an opaque device-derived code, with no online HWID upload by the activation flow. The generator and owner master-key file are not published. Compact offline verification is not a guarantee against reverse engineering or application tampering. Existing saved settings, temperature/cooling behavior and the System/Graphite input inversion are retained.

[Windows x64 EXE](downloads/VRAM-GPU-Desk-1.24-Setup-x64.exe) · [ZIP](downloads/VRAM-GPU-Desk-1.24-Installer.zip)

# VRAM GPU Desk 1.23

## New in 1.23 — compact numeric controls and consistent theme contrast

**Seven numeric fields use horizontal −/+ controls.** Temperature target, overheat-warning threshold, idle-cooling target, minimum fan percentage, emergency GPU-load percentage, refresh interval and overlay scale share compact controls with inline units and a thin color accent. Keyboard entry and dynamic model limits, including reported hardware bounds, are retained.

**Matching inputs in both themes.** The language, theme and GPU selectors, search field and quick-button editor follow the same accent style. The System theme uses white input backgrounds with dark text; Graphite uses dark input backgrounds with light text. Focused, selected and disabled states and dropdown popups follow the active theme.

**Higher configured thresholds stand out.** The soft temperature target uses red text when set **above 80 °C (81 °C and higher)**; the overheat-warning threshold uses red text from **86 °C**. These colors describe the **configured threshold**, not the current GPU temperature or a live temperature alarm. Control algorithms, the 78/85 °C default target/warning values and saved preferences are unchanged. Persistent recovery, the application log and maximum-pin/total PSU-current labels from 1.22 are retained.

[System theme — light fields](images/temperature-fields-light.png) · [Graphite theme — dark fields](images/temperature-fields-dark.png)

Windows x64 EXE — `VRAM-GPU-Desk-1.23-Setup-x64.exe` · Installer ZIP — `VRAM-GPU-Desk-1.23-Installer.zip`

# VRAM GPU Desk 1.22

## New in 1.22 — persistent recovery, application log and clearer PSU current

**Persistent control recovery.** While Force control recovery is enabled, checked retries continue without a retry-count limit: after 5, 10, 30, then every 60 seconds. The latest ON/OFF choice is retained through controller stop and restart. A nonmodal loss warning closes automatically only after fresh telemetry confirms recovery. Native ownership, teardown and hardware-limit checks remain in force; this does not provide exclusive control over MSI Afterburner or another controller.

**Application log.** A separate button opens a log of per-GPU control loss, recovery and retry events, plus initial states and changes of all control-related checkboxes. Each record includes UTC and local timestamps. Temperature logging starts at **78 °C**, records subsequent whole-degree changes, and marks the return below 78 °C. The viewer shows up to 500 events from the current session. UTF-8 files persist locally at `%LOCALAPPDATA%/VRAMDeskJava/logs/application.log`, rotating at 2 MiB with five archives.

**Maximum pin current or connector total.** For each of up to two physical PSU GPU-power ports, the card shows the maximum of the available individual pin-current readings if at least one is known, including incomplete pin data. If no individual readings are available, it shows the measured connector total instead. Labels explicitly distinguish **max** and **total**. Unknown sensors remain —; a measured zero stays zero. Tooltips retain individual pin readings and the total when available. A rail current is not substituted for a connector measurement.

**Updating from an old 1.9 installation.** An older copy under LocalAppData can remain running even when 1.22 has installed correctly in Program Files, making the old interface appear to lack newer settings. Before setup, exit the old copy through its tray menu; after setup, use the current Start menu shortcut and check **v1.22**. If a shortcut still points to the old folder, use the installed Program Files copy and correct that shortcut. An old running window does not mean the new controls were removed.

Windows x64 EXE — `VRAM-GPU-Desk-1.22-Setup-x64.exe` · Installer ZIP — `VRAM-GPU-Desk-1.22-Installer.zip`

# VRAM GPU Desk 1.21

## New in 1.21 — optional PSU telemetry and automatic overlay contrast

**Optional layout.** When PSU monitoring is OFF or no compatible PSU is detected, the PSU card is hidden and the other cards use the available width, without an empty placeholder. Once a PSU has been detected, temporarily unavailable readings keep its card visible with dashes.

**More compact dashboard.** The “Time with VRAM > 50%” card has been removed from both single- and dual-GPU layouts. The 30-day application ranking and stored history are retained.

**Optional PSU monitoring is OFF by default.** Enable it with the separate settings checkbox to add a PSU card beside the existing indicators. It shows available output power and up to two actual GPU power-connector current groups. Missing or stale measurements display —; rail currents are not presented as individual GPU connector readings. Read-only PSU queries use a separate protected component installed with the application's one-time UAC setup; they do not acquire GPU control.

**Compatibility is model-specific.** Read-only telemetry was verified on an MSI MPG Ai1300TS. Ai1600TS is protocol-qualified. Selected Corsair HXi/RMi, Thermaltake DPS G/iRGB PLUS and additional NZXT E-series readers passed synthetic protocol checks; their physical hardware validation is pending. Corsair provides measured output watts; Thermaltake's rail-derived total is explicitly marked calculated; NZXT provides rail data without inventing a total. be quiet! Dark Power Pro 14 IO is researched; Seasonic OptiGuard and ASUS products have no qualified reader in this release. This is not universal support for six brands. See [PSU compatibility](docs/psu-compatibility.md).

**Automatic overlay text contrast is ON by default.** Text adapts to the background; turn the option off to retain manual light/dark text selection. Transparent backgrounds, compact gauges, separate overlays for two NVIDIA GPUs, double-click to open the main window, saved positions and temperature colors/alarms are retained.

The graphite screenshots below use synthetic demonstration readings, including PSU values. GPU settings, process actions, emergency modes and existing saved choices retain their behavior.

Windows x64 EXE — `VRAM-GPU-Desk-1.21-Setup-x64.exe` · Installer ZIP — `VRAM-GPU-Desk-1.21-Installer.zip`

# VRAM GPU Desk 1.20.1

Double-click either GPU overlay with the left mouse button to open the main application, including from the tray or minimized state. Works with locked and unlocked overlays; dragging does not trigger opening. Existing settings, controls and quick buttons are preserved. The overlay settings dialog includes localized guidance in all12languages.

# VRAM GPU Desk 1.20

- Compact transparent GPU overlay: three filling gauges for VRAM occupancy, GPU load and temperature. No background panel; above ordinary Windows windows without taking keyboard focus.
- Default size: ≈164 × 114 physical pixels per NVIDIA card, independent of Windows DPI scaling. 75–200% size adjustment; bold outlined numbers; position lock and light/dark text.
- Two NVIDIA GPUs have separate movable overlays with independently saved positions.
- Temperature colors: ≤40 °C green;41–75 yellow;76–81 orange;82–86 red;≥87 bright red with blinking fill. Numbers remain visible.
- At ≥88 °C a short beep repeats every3seconds. Sound defaults ON, can be disabled separately, and remains independent of overlay visibility. Stale/missing telemetry cancels sound.
- Floating display defaults OFF. Settings available from the dashboard and tray; positions and choices persist.
- Existing NVIDIA control, process actions and both emergency modes retain their behavior. Second GPU control remains experimental. GPU controllers such as MSI Afterburner may conflict when modifying the same settings.
- Windows x64;12 languages; English is the main description. Installation of the control component requires one UAC confirmation.

The overlay uses existing telemetry; it performs no additional GPU control. Protected UAC/lock-screen and exclusive-fullscreen display are not guaranteed. The private CUDA-quota prototype is separate and is not included in1.20.
