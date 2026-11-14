# VRAM GPU Desk

[English](README.md) · [Русский](README.ru.md) · [Deutsch](README.de.md) · [Español](README.es.md) · [Français](README.fr.md) · [Italiano](README.it.md) · [简体中文](README.zh.md) · [한국어](README.ko.md) · [日本語](README.ja.md) · [العربية](README.ar.md) · [हिन्दी](README.hi.md) · [Tiếng Việt](README.vi.md)

**Local NVIDIA GPU memory monitoring and temperature control for Windows x64. NVIDIA GPUs only; AMD and Intel GPUs are not supported.**

Version **1.14** · [Download Windows installer](downloads/VRAM-GPU-Desk-1.14-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.14-Installer.zip)

![VRAM GPU Desk — graphite theme](images/dashboard-graphite.png)

The armed state is shown only as an illustration. This emergency option is OFF at every launch.


> **GPU control:** GPU temperature parameter control requires one UAC confirmation when installing the control component. Subsequent enabling of temperature control and cooling proceeds without further UAC prompts. Monitoring itself does not require UAC.

> **Concurrent GPU control:** GPU temperature parameter control may conflict with other programs that change power limits, clocks or fan speeds at the same time, such as MSI Afterburner. Use only one active controller for these settings. This warning concerns simultaneous changes to settings, not passive monitoring.



## Planned dual-GPU support — experimental

Work in progress for 1.15: separate panels for two supported NVIDIA GPUs, with independent settings and metrics. Control of the second NVIDIA GPU is experimental. A mixed-vendor configuration uses one NVIDIA panel. The download links on this page still point to released 1.14; this roadmap does not announce a 1.15 release.

## New in 1.14: compact workspace and easier updates

**Graphite Studio (1.12).** All primary settings and actions stay visible together at 1200×900: seven process columns, at least six rows, four graphs and the complete top-10 legend. Process names use a high-contrast 14 px bold font. New profiles start in Graphite; an explicitly saved System or Graphite theme is preserved. Four editable one-click buttons retain their exact process-instance bindings and Close/Terminate actions.

**Visible cooling hysteresis (1.13).** The cooling panel now shows the fixed **4 °C** hysteresis. Its tooltip explains 32→36 °C and 35→39 °C examples. This makes the existing rule visible without changing the cooling algorithm.

**Installer flow (1.14).** Setup asks permission to close the running target copy. With consent it requests normal JVM shutdown through Windows Restart Manager, waits for the app, its launcher and controller files to be released, then continues. It targets verified instances of this installation, without forced termination. Declining, cancellation, a shutdown veto, remaining locks or a timeout blocks replacement; silent setup does not close a running app automatically.

The final **Launch VRAM GPU Desk** checkbox is checked by default and can be cleared. Launch uses normal rights for the same signed-in user; if that context is unavailable, use the normal Start menu shortcut. This is a one-time launch after installation; the saved Windows startup choice is preserved.

Verified for 1.14: **9 installer-flow cases, 107 Restart Manager/JDK checks and 17 fixed-launch gate checks**, all **166 package files and 88 Java classes**, broker pins, Unicode paths and the bundled-runtime launcher.

## New in 1.11: emergency GPU-load process termination

A separate checkbox is **OFF at every launch**. After confirmed temperature stays strictly above the configured overheat threshold for **10 seconds**, it can terminate accessible processes that have loaded the selected GPU at or above **20% by default (adjustable 10–100%) for at least 3 seconds**. This uses the process’s busiest GPU engine, **not VRAM allocation**. It is one-shot and switches OFF after the attempt; another attempt needs explicit reactivation. Confirmed process-load data and a valid sensor are required.

**Warning: this may terminate useful as well as unwanted applications and lose unsaved work.** Fresh temperature, GPU identity, PID, creation time, EXE path and the same process handle are checked. Protected Windows/NVIDIA components, critical or unverifiable processes and the utility itself are excluded. It does not terminate process trees, stop services or request more elevation. The older selected-application emergency option remains separate. This is an additional measure, not a guarantee against GPU damage.

Verified for 1.11: **40 native CPU checks**, **256 Java/catalog/guard checks**, **673 UI assertions in 48 cases** across twelve languages and two themes, read-only access to **710 valid PDH counter instances**, independent native review, all **164 package files**, **87 compiled Java classes**, embedded broker pins, isolated installation/uninstallation, and the packaged Unicode launcher with its bundled runtime.


## What it does

- Shows physical VRAM used/free, GPU utilization and GPU temperature, with compact history graphs.
- Lists local applications and services using GPU memory, with search, sorting and an optional **over 0.5 GiB** filter.
- Displays the top 10 applications and an “Others” category as normalized shares over the last 30 days of observed samples. Percentages sum to 100%; this is a historical allocation of recorded process-memory readings, not an additive breakdown of physical VRAM.
- Shows the percentage of valid observed time in the last 24 hours with physical VRAM occupancy above 50%. Monitoring gaps are excluded.
- Exports a UTF-8 CSV report to a chosen local path.
- Minimizes to the system tray, restores the existing window on repeat launch, and supports optional Windows startup.
- Offers system and dark graphite themes, 12 interface languages, and a configurable 1–5 second UI refresh interval (default: 2 seconds).
- Provides optional soft GPU temperature control through supported power and core-clock limits; protection runs independently of the UI refresh interval.
- Provides idle cooling, fan RPM indicators, and animated fan icons. Fresh settings request both temperature control and idle cooling on; a previously saved manual OFF is preserved. Active control is shown only after a confirmed connection.
- Can show an alert after temperature stays strictly above the selected 75–92°C threshold for at least 10 seconds. Short spikes do not produce an alert.
- Provides a separate, initially disabled emergency option for the explicitly selected application. Closing or terminating an application can lose unsaved work; protected or unverifiable processes cannot be selected for this action.


![VRAM GPU Desk — system theme](images/dashboard-system.png)

## Four quick action buttons

Assign **Close application** or **Terminate process** to one of four compact buttons, and reassign it through the adjacent `⋮` menu. Each binding refers to the explicitly selected process instance: PID, creation time and executable path. When that instance ends, a neighboring process or a reused PID is not selected automatically.

A configured button executes with one click **without an additional confirmation**. Closing or terminating a process may lose unsaved work. Native checks for protected, critical or unverifiable processes remain in place. The separate emergency option is initially off and retains its existing selected-application behavior.


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

Windows 10/11 x64, .NET Framework 4.8 and a supported NVIDIA driver. The installer includes its Java runtime, so a separate Java installation is not required. The signed-in Windows user must be an administrator using a normal filtered desktop token. Setup requests UAC once and installs the control component in a fixed protected Program Files directory; entering credentials for a different administrator is not supported. Two protected, demand-only tasks use fixed control launchers and typed local communication. The installed channel is designed to start control without a further UAC prompt; if it cannot be authenticated, control stays unavailable instead of falling back to another elevation prompt. Driver versions and DLL hashes are not allowlisted. The installed system NVML library must pass offline Windows signature verification with a verified NVIDIA Corporation signer, safe-path checks and the required API checks. Driver updates do not require adding a new version or hash. Offline trust verification can fail when required trust data is not available locally; no certificates or drivers are downloaded by the application.

## Installation and privacy

1. Download the installer and compare its SHA-256 with [SHA256SUMS.txt](SHA256SUMS.txt).
2. Run setup normally from the signed-in administrator account and approve UAC. If the target copy is running, answer its shutdown question; setup continues after normal exit and released files. The protected installation folder is fixed.
3. Open the new VRAM GPU Desk shortcut, select the GPU and check the confirmed controller status. Configure the controls and quick buttons as needed. Settings are saved locally; saved OFF choices remain OFF.

The application uses local Windows/GPU interfaces. It contains no designed-in telemetry uploads, cloud inference, updater or runtime model downloads. CSV files, history and settings remain local. This is **not** a claim of OS-wide network isolation or a guarantee about third-party drivers, Windows diagnostics or synchronization software.

The installer is unsigned. The application is distributed as compiled binaries; **application source code is not published in this repository**. Java bytecode is not encrypted or guaranteed to resist decompilation. Third-party runtime license notices are retained in the installed runtime.

Screenshots use synthetic demonstration data and simulated controller state. They illustrate the interface and do not demonstrate hardware operation or performance.

## Changes in 1.10

- Adds four configurable, process-instance-bound quick buttons for one-click close or terminate, with reassignment and preserved native safety checks.
- Uses smaller dashboard descriptions and increases mini-graph height from 35 to 55 pixels; keeps the high-contrast tray icon.
- Installs a protected control component once with UAC. Fresh thermal and idle-cooling settings are on; saved manual OFF choices are preserved.
- Includes the conservative adapter-alias correction: confirmed non-render indirect-display aliases are excluded without merging separate physical GPUs by name or memory values.
- Repairs safe incomplete installations and reports a concrete setup phase, code and HRESULT when component setup fails.
- Preserves both themes, 12 languages, local history, UTF-8 CSV, GPU identity checks and existing lease/watchdog/restore policies.

Verified for this release: 48 isolated interface cases across 12 languages and two themes, tray icons, settings defaults, quick-action binding/runner checks, actual CLR token checks, Unicode paths, all 163 package files and embedded broker pins, isolated installation/uninstallation, and a real elevated temporary Task Scheduler registration test with XML/DACL readback, rollback and cleanup. The temporary tasks were **not run**.

Screenshots use synthetic demonstration data and simulated controller state, without demonstrating hardware operation or performance.

## License

Free for noncommercial use under [PolyForm Noncommercial 1.0.0](LICENSE.md), subject to its terms and notice requirements. Commercial use requires separate permission. This is not an open-source license; application source code is not published. Third-party runtime licenses remain unchanged.
