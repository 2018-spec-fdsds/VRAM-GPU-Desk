# Distribution

Current version: **1.18**, Windows x64.

- [EXE installer](downloads/VRAM-GPU-Desk-1.18-Setup-x64.exe)
- [Installer ZIP](downloads/VRAM-GPU-Desk-1.18-Installer.zip)
- [SHA-256 index](SHA256SUMS.txt)
- [Release notes](RELEASE-NOTES.md)

The ZIP contains the same EXE installer, checksum, instructions and license. Java is included. It is an installer bundle; copying the archive does not register the protected Windows control component.

## Installation and launch

Run setup normally from the signed-in administrator account and approve its one-time UAC prompt. The Program Files location is fixed and protected. Entering another administrator's credentials is not supported.

If a verified target copy is running, setup asks whether to close it normally. With consent, Windows Restart Manager requests normal JVM shutdown, and setup waits for the application, launcher and controller files to be released. No forced process termination is used. Refusal, cancellation, veto, timeout or remaining file locks prevents replacement; manual tray Exit and retry remain available.

The final **Launch VRAM GPU Desk** checkbox is checked by default and can be cleared. A fixed native gate verifies normal rights and the same interactive user before starting the app. If the required normal context is unavailable, launch it with the normal Start menu shortcut. Silent setup neither closes a running application automatically nor launches the app afterward. This checkbox preserves the separate saved Windows startup choice.

GPU temperature control requires one UAC confirmation when installing the control component. Subsequent enabling of temperature control and cooling uses that installed channel without further UAC prompts. Monitoring itself does not require UAC.

## NVIDIA panels and recovery

NVIDIA GPUs only; AMD and Intel controls are unsupported. Model/driver capabilities still determine available controls. Two supported NVIDIA GPUs use independent panels and settings; control of the second NVIDIA GPU is experimental. One NVIDIA plus AMD/Intel uses one NVIDIA panel. The process/history GPU filter does not retarget either controller.

Control loss shows a warning and manual Retry. Force control recovery defaults ON for new or missing settings; explicitly saved OFF is preserved. Recovery is saved per GPU and uses 5/10/30/60-second backoff after confirmed teardown and fresh same-GPU data. It retains native safety checks and cannot provide exclusive control against MSI Afterburner. Both emergency options remain OFF at each launch. See the feature descriptions in the [English README](README.md).

The verified 1.18 package contains 167 manifest files and 106 Java classes. One-GPU minimum is 1200×900; the current two-GPU workspace requires 1920×1050.

## Shared RAM and CPU dashboard

System RAM shows physical memory used/total in GiB, usage percentage, available memory and a five-minute graph. Its total is physical RAM usable by Windows, separate from VRAM and page-file commit.

The CPU card shows overall utilization, physical-core and logical-thread counts, and an instantaneous utilization bar for each physical core. Core bars group their logical threads; overall load is weighted by logical processors. Built-in Windows measurements need no extra UAC prompt, driver or external monitoring application. Missing, invalid or more than six-second-old readings are unavailable: RAM shows a gap in its history graph; CPU shows **—** and unavailable core bars.

With one GPU, all six metric cards remain together at 1200×900. With two supported NVIDIA GPUs, the minimum is 1920×1050: each GPU has a four-card 2×2 block with aligned readings and complete controls. Thin vertical dividers separate the GPU areas and shared right column, with RAM above the taller CPU card. RAM and CPU appear only once, independently of GPU selection. All three fan indicators stay visible by wrapping when needed; fan-control logic is unchanged.

## Window behavior

The saved **Minimize to tray** checkbox is enabled by default. Turn it off to minimize the window to the Windows taskbar. This does not change the separate Windows startup choice or the close-button behavior.

## Package integrity

Compare the downloaded file's SHA-256 with [SHA256SUMS.txt](SHA256SUMS.txt) or its adjacent .sha256 file. The installer does not carry a personal publisher certificate.

## License and contents

The repository distributes compiled application binaries, documentation and synthetic demonstration screenshots. Application sources are not published. Use is governed by [PolyForm Noncommercial 1.0.0](LICENSE.md); commercial use requires separate permission. Preserve the terms and notices. Third-party components retain their own runtime license notices.

