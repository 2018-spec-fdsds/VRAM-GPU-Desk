# VRAM GPU Desk

**Local GPU memory monitoring and temperature control for Windows x64.**

Version **1.4** · [Русское описание](README.ru.md) · [Download Windows installer](downloads/VRAM-GPU-Desk-1.4-Setup-x64.exe)

![VRAM GPU Desk — system theme](images/dashboard-system.png)

## What it does

- Shows physical VRAM used/free, GPU utilization and GPU temperature, with compact history graphs.
- Lists local applications and services using GPU memory, with search, sorting and an optional **over 0.5 GiB** filter.
- Displays the top 10 applications and an “Others” category as normalized shares over the last 30 days of observed samples. Percentages sum to 100%; this is a historical allocation of recorded process-memory readings, not an additive breakdown of physical VRAM.
- Shows the percentage of valid observed time in the last 24 hours with physical VRAM occupancy above 50%. Monitoring gaps are excluded.
- Exports a UTF-8 CSV report to a chosen local path.
- Minimizes to the system tray, restores the existing window on repeat launch, and supports optional Windows startup.
- Offers system and dark graphite themes, 12 interface languages, and a configurable 1–5 second UI refresh interval (default: 2 seconds).
- Provides optional soft GPU temperature control through supported power and core-clock limits; protection runs independently of the UI refresh interval.
- Provides optional idle cooling, fan RPM indicators, and animated fan icons.
- Can show an alert after temperature stays strictly above the selected 75–92°C threshold for at least 10 seconds. Short spikes do not produce an alert.
- Provides a separate, initially disabled emergency option for the explicitly selected application. Closing or terminating an application can lose unsaved work; protected or unverifiable processes cannot be selected for this action.

![VRAM GPU Desk — graphite theme](images/dashboard-graphite.png)

## Temperature targets and hysteresis

Some settings deliberately use separate stop/restart thresholds and short waiting periods. This avoids rapid switching when a reading fluctuates by a few degrees.

| Setting | Actual behavior | Why |
|---|---|---|
| Idle target, default **32°C** (28–40°C adjustable) | During idle, after temperature stays at or below 32°C for 3 seconds, control returns to firmware AUTO. Cooling restarts at 36°C, which is target +4°C. With a 35°C target, the corresponding restart point is 39°C. | The 4°C hysteresis prevents repeated fan starts and stops around one threshold. Firmware AUTO, rather than the application, decides whether fans stop completely. |
| Idle/load classification | At GPU utilization up to 10%, idle behavior is allowed. From 15%, the load cooling curve applies. Between 11% and 14%, the previous classification is retained. Unknown utilization keeps cooling active. | The gap avoids toggling between idle and load due to small utilization fluctuations. |
| Soft temperature target, 70–88°C | Power and core-clock limits adjust gradually using temperature trend, with an operating band around the target. Actual temperature can be somewhat below the target or briefly exceed it. | Thermal inertia, sensor updates and driver limits make an exact hard ceiling impossible. The target is a control goal, not an emergency cutoff. |
| Overheat alert | The reading must remain strictly above its threshold for at least 10 seconds. | Suppresses short temperature spikes. |

Idle temperature is **not** the temperature limit under sustained load. Ambient conditions, board firmware and driver restrictions affect attainable temperatures and fan response. Do not run competing fan or clock controllers against the same card at the same time.

## Hardware and requirements

For NVIDIA GeForce **RTX 5000 Series** GPUs. Monitoring and available controls depend on the GPU and driver; unsupported controls remain unavailable rather than being simulated.

Windows 10/11 x64, .NET Framework 4.8 and a supported NVIDIA driver. The installer includes its Java runtime, so a separate Java installation is not required. GPU control may require a normal Windows UAC confirmation. A changed driver revision may require a reviewed application update because the GPU control library is verified before use.

## Installation and privacy

1. Download the installer and compare its SHA-256 with [SHA256SUMS.txt](SHA256SUMS.txt).
2. Run the installer for the current Windows user and choose a local folder.
3. Open VRAM GPU Desk, select the GPU and configure optional controls. Settings are saved locally.

The application uses local Windows/GPU interfaces. It contains no designed-in telemetry uploads, cloud inference, updater or runtime model downloads. CSV files, history and settings remain local. This is **not** a claim of OS-wide network isolation or a guarantee about third-party drivers, Windows diagnostics or synchronization software.

The installer is unsigned. The application is distributed as compiled binaries; **application source code is not published in this repository**. Java bytecode is not encrypted or guaranteed to resist decompilation. Third-party runtime license notices are retained in the installed runtime.

Screenshots use synthetic demonstration data, not a private application list. They illustrate the interface, not a performance benchmark.
