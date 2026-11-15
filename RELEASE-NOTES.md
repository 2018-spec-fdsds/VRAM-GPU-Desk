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
