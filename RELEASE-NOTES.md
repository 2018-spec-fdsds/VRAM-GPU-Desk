# VRAM GPU Desk 1.21

## New in 1.21 — optional PSU telemetry and automatic overlay contrast

**Optional layout.** When PSU monitoring is OFF or no compatible PSU is detected, the PSU card is hidden and the other cards use the available width, without an empty placeholder. Once a PSU has been detected, temporarily unavailable readings keep its card visible with dashes.

**More compact dashboard.** The “Time with VRAM > 50%” card has been removed from both single- and dual-GPU layouts. The 30-day application ranking and stored history are retained.

**Optional PSU monitoring is OFF by default.** Enable it with the separate settings checkbox to add a PSU card beside the existing indicators. It shows available output power and up to two actual GPU power-connector current groups. Missing or stale measurements display —; rail currents are not presented as individual GPU connector readings. Read-only PSU queries use a separate protected component installed with the application's one-time UAC setup; they do not acquire GPU control.

**Compatibility is model-specific.** Read-only telemetry was verified on an MSI MPG Ai1300TS. Ai1600TS is protocol-qualified. Selected Corsair HXi/RMi, Thermaltake DPS G/iRGB PLUS and additional NZXT E-series readers passed synthetic protocol checks; their physical hardware validation is pending. Corsair provides measured output watts; Thermaltake's rail-derived total is explicitly marked calculated; NZXT provides rail data without inventing a total. be quiet! Dark Power Pro 14 IO is researched; Seasonic OptiGuard and ASUS products have no qualified reader in this release. This is not universal support for six brands. See [PSU compatibility](docs/psu-compatibility.md).

**Automatic overlay text contrast is ON by default.** Text adapts to the background; turn the option off to retain manual light/dark text selection. Transparent backgrounds, compact gauges, separate overlays for two NVIDIA GPUs, double-click to open the main window, saved positions and temperature colors/alarms are retained.

The graphite screenshots below use synthetic demonstration readings, including PSU values. GPU settings, process actions, emergency modes and existing saved choices retain their behavior.

[Windows x64 EXE](downloads/VRAM-GPU-Desk-1.21-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.21-Installer.zip)

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
