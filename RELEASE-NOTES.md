# VRAM GPU Desk — release notes

## 1.19

[Windows x64 installer](downloads/VRAM-GPU-Desk-1.19-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.19-Installer.zip) · [SHA-256](SHA256SUMS.txt)

### Per-device control for NVIDIA RTX 30, 40 and 50

- Capture each GPU’s actual power bounds and starting limit independently. The session ceiling and restoration baseline use that starting limit, not a factory default or reference board wattage.
- Acquiring control performs no initial power or clock write. Power adjustment scales at 1% of the session baseline per second, within actual bounds and the session ceiling.
- Optional clock control uses a validated supported range. Unsupported clocks do not remove independently supported power-only control; valid temperature can support power-only regulation even with unknown GPU utilization.
- Block targets above reported hardware temperature limits and leave missing limits unknown. Unsupported operations remain visible as unavailable, with per-device reasons.
- Recover fans independently of the power client. BIOS, OEM, driver and laptop differences still determine supported operations; second-GPU control remains experimental.

### Compact CPU area with two GPUs

The CPU card’s bottom now aligns with the adjacent idle-cooling panel, above the emergency and recovery rows. RAM remains at the top, while CPU utilization and physical-core bars remain visible. This changes only the dual-GPU CPU area; the single-GPU six-card layout is unchanged.

### Published reference data

The [reference documentation](docs/nvidia-rtx30-plus/README.md) and [UTF-8 CSV](docs/nvidia-rtx30-plus/REFERENCE-GPUS.csv) contain 45 model/variant groups: 27 desktop and 18 laptop. These are documentary reference groups, not 45 hardware tests. Published board power and laptop TGP are not executable control presets. The RTX 3060 Ti 200 W row is explicitly a reference specification, not a claim covering every GDDR6X or OEM variant. Official NVIDIA sources are linked in the reference document.

### Retained workspace and safeguards

Keep system RAM’s five-minute graph, CPU’s instantaneous physical-core bars, six single-GPU cards and the aligned two-GPU workspace. Both emergency options remain OFF at every launch; new or missing recovery settings default ON while saved OFF remains respected. Optional tray minimization, all twelve languages and both themes remain available.

The protected control component requires one UAC approval at installation. Concurrent GPU parameter changes may conflict with MSI Afterburner or another active controller; exclusive ownership is not guaranteed. English remains the main description, Graphite the first screenshot. Application sources are not published and use remains governed by [PolyForm Noncommercial 1.0.0](LICENSE.md).

---

## 1.18

[Windows x64 installer](downloads/VRAM-GPU-Desk-1.18-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.18-Installer.zip) · [SHA-256](SHA256SUMS.txt)

### CPU utilization and physical-core bars

- The CPU card shows total utilization, physical-core and logical-thread counts, and an instantaneous utilization bar for each physical core.
- Core bars group their logical threads. Overall utilization is weighted by logical processors, rather than an unweighted mean of core groups.
- Uses built-in Windows CPU measurements without another UAC prompt, driver or provider application. Missing, invalid or more than six-second-old CPU readings show **—** and unavailable core bars.

### Aligned two-GPU workspace

- A single GPU retains six metric cards at 1200×900: four GPU cards, system RAM and CPU.
- The two-NVIDIA-GPU minimum is now **1920×1050**. Each GPU has a four-card **2×2** block, aligned readings and all its controls. Thin vertical dividers separate the GPU areas from the shared right column.
- RAM appears above a taller CPU card in that shared column. Both are system-wide, appear only once and are independent of GPU selection. Second-GPU control remains experimental.
- All three fan indicators remain visible by wrapping when space is limited. Fan-control logic is unchanged.

The verified 1.18 package contains 167 manifest files and 106 Java classes.

### Retained features and distribution

All twelve languages, Graphite and System themes, readable process rows, compact editable quick buttons and existing controls remain available. Recovery defaults ON for new or missing settings; explicitly saved OFF is respected. Both emergency options remain OFF at each launch. Optional tray minimization still allows ordinary Windows taskbar minimization.

The protected NVIDIA control component requires one UAC approval at installation. CPU and RAM monitoring require no additional elevation. Concurrent GPU parameter changes may conflict with MSI Afterburner or another controller. English remains the main description and Graphite the first screenshot. Application sources are not published; use remains governed by [PolyForm Noncommercial 1.0.0](LICENSE.md).

---

## 1.17

[Windows x64 installer](downloads/VRAM-GPU-Desk-1.17-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.17-Installer.zip) · [SHA-256](SHA256SUMS.txt)

### System RAM alongside GPU metrics

- A fifth **System RAM** card shows used/total physical memory in GiB, usage percentage, available memory and a five-minute history graph.
- The total is the physical RAM usable by Windows. It is separate from VRAM and page-file commit, and does not change when another GPU is selected.
- With two NVIDIA panels, system RAM appears once in the primary five-card panel. The second panel retains its four GPU cards, independent settings and experimental control status.
- Missing, invalid or more than six-second-old readings display **—** and leave a gap in the graph. RAM uses the existing refresh interval and needs no UAC prompt.
- Compact process rows, all GPU controls, quick-button management, all twelve languages and both themes remain available.

The verified 1.17 package contains 167 manifest files and 98 Java classes.

### Retained behavior

Force control recovery defaults ON for new or missing settings, while an explicitly saved OFF is respected. Both emergency termination options remain OFF at each launch. The saved Minimize to tray choice still supports ordinary Windows taskbar minimization when disabled.

The NVIDIA control component requires one UAC approval at installation; RAM monitoring does not require elevation. Simultaneous power, clock or fan control may conflict with MSI Afterburner or another active controller. Second-NVIDIA-GPU control remains experimental. English is the main description, Graphite is the first demonstration image, and the application remains licensed under [PolyForm Noncommercial 1.0.0](LICENSE.md).

---

## 1.16

[Windows x64 installer](downloads/VRAM-GPU-Desk-1.16-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.16-Installer.zip) · [SHA-256](SHA256SUMS.txt)

### Control recovery and communication

- Force control recovery now defaults **ON** for new or missing settings. Explicitly saved OFF choices remain respected. Recovery is stored separately for each GPU; both emergency termination options remain **OFF at every launch**.
- The Java request deadline now allows the native channel to finish its bounded response. The operational watchdog starts its heartbeat after successful GPU acquisition; its six-second safety limit remains enforced.
- Timed-out or cached readings no longer refresh confirmed telemetry. Stale fan readings display as unavailable, and communication loss is explained separately from a confirmed external parameter change.
- A bounded local metadata journal preserves errors and slow-response timing across reconnections. Connection secrets and user process contents are not recorded in it.
- Recovery retains GPU identity, lease, ownership, readback and conditional-restore checks. It does not guarantee exclusive control against MSI Afterburner or another active GPU controller.

### Optional ordinary minimization

- The saved **Minimize to tray** checkbox appears in the header. It is enabled by default; turn it off to minimize to the Windows taskbar like a normal application.
- Compact controls, readable process names, four editable quick buttons, all twelve languages and both themes remain available. One NVIDIA GPU uses one panel; two supported NVIDIA GPUs have independent panels, with **second-GPU control experimental**.

### Distribution

The installer includes Java and preserves preferences and exact-instance quick-button bindings during updates. Installation of the protected control component requires one UAC confirmation; subsequent control uses the installed channel. English remains the main description and Graphite the first demonstration image.

The package contains 167 manifest files and 96 Java classes. Checks cover current communication, settings and UI fixtures, packaged Unicode launch and isolated installation/uninstallation. Licensed under [PolyForm Noncommercial 1.0.0](LICENSE.md); third-party runtime notices are retained. Application sources are not published.

---

## 1.15 (historical defaults; 1.16 changes recovery to ON)

[Windows x64 installer](downloads/VRAM-GPU-Desk-1.15-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.15-Installer.zip) · [SHA-256](SHA256SUMS.txt)

### Independent NVIDIA panels
- Two supported NVIDIA GPUs have independent metrics, four graphs per card, control clients and saved settings. **Second NVIDIA GPU control is experimental.** A mixed NVIDIA + AMD/Intel configuration uses one NVIDIA panel.
- Physical PCI/vendor/device identity fixes each panel to its GPU. Reordering or changing the shared process/history filter does not reassign control. A missing known GPU remains unavailable instead of being replaced by a different device.
- One-GPU minimum remains 1200×900. Two panels use a 1600×950 minimum so that settings, six process rows and compact shared quick buttons remain visible.

### Compact quick-button management
- Four compact buttons remain in one horizontal row, with one shared `⋮` menu containing slot submenus.
- Assign/reassign, rename without rebinding and clear remain accessible for missing targets. Custom labels survive reassignment; captions fit the available width and tooltips retain the full name.
- Actions keep exact process PID/creation/path binding and native protected-process checks. A configured action remains one click without another confirmation; unsaved work can be lost.

### Control loss and recovery
- Control loss shows a warning and manual Retry. Desired modes and saved manual OFF choices are preserved separately from confirmed Active status.
- **Force control recovery is OFF by default and saved per GPU.** If enabled, retries use 5/10/30/60-second backoff and require confirmed previous-client teardown, fresh same-GPU readings and a new native lease grant.
- Native GPU identity, bounds, ownership, readback, watchdog and conditional restore checks remain enforced. This does not provide exclusive control or prevent MSI Afterburner from changing settings.
- Manual OFF cancels automatic retries. Manual retry can refresh an inactive verified client before a later explicit ON. Both emergency modes remain OFF at each launch.

### Retained interface and installer improvements
- Graphite Studio keeps primary controls visible, high-contrast 14 px bold process names, four memory/load/temperature/history graphs and a complete top-10 legend. Both themes and all 12 languages remain available.
- The fixed 4 °C idle-cooling hysteresis is visible; the underlying cooling rule is unchanged.
- Setup asks before closing verified copies, uses normal JVM shutdown without force, waits for released files and refuses replacement on cancellation, veto, timeout or locks.
- The final launch checkbox is checked by default and launches with normal rights for the same signed-in user. This does not alter the separate Windows startup choice. The protected component requires one UAC approval at installation; subsequent control uses its authenticated channel.

### Verification and package
Verification includes **2262 UI checks**, **215 native checks**, **61 client lifecycle/I/O checks**, **48 recovery-coordinator checks**, **43 per-GPU settings checks**, all **167 package files** and **93 Java classes**, embedded broker pins, Unicode paths, isolated installation/uninstallation, locked-JAR refusal, retained user files and the bundled-runtime launcher. Synthetic screenshots show current 1.15.

The ZIP bundles the same installer, checksum, instructions and license. English is the default README; all 12 descriptions retain the full feature history, with Graphite first. Licensed under [PolyForm Noncommercial 1.0.0](LICENSE.md); third-party runtime notices are retained. Application sources are not published.

---

## 1.14

[Windows x64 installer](downloads/VRAM-GPU-Desk-1.14-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.14-Installer.zip) · [SHA-256](SHA256SUMS.txt)

### Easier installation and updates
- Setup asks before closing verified running copies of the target installation, including a validated legacy Java installation where applicable.
- Windows Restart Manager is used with process identities only and without forced shutdown. Setup waits for the JVM, its launcher and controller files to be released before replacing files.
- No, Cancel, application veto, remaining locks and timeout prevent replacement. Silent setup does not automatically close a running copy.
- The final **Launch VRAM GPU Desk** checkbox is checked by default and can be cleared. A fixed native gate starts the app with normal rights for the same signed-in user. If that context is unavailable, use the normal Start menu shortcut.
- This one-time launch is separate from the saved Windows startup setting.

### Included interface improvements
- **1.12 — Graphite Studio:** all primary settings and actions remain visible at 1200×900, with seven process columns, at least six rows, four graphs and the full top-10 legend. Process names are high-contrast 14 px bold. New profiles use Graphite; an explicit saved theme is preserved.
- **1.13 — visible cooling hysteresis:** the fixed 4 °C difference is displayed with 32→36 °C and 35→39 °C examples. The cooling algorithm is unchanged.
- Four editable quick buttons retain exact process-instance Close/Terminate bindings. Both emergency options remain OFF at each launch; GPU-load emergency termination remains one-shot.

### Verification and distribution
Verification covered 9 installer-flow profiles, 107 Restart Manager/JDK checks, 17 fixed-launch gate checks, all 166 package files and 88 Java classes, embedded broker pins, Unicode paths, isolated installation/uninstallation and the bundled-runtime launcher. Existing UI behavior was compared with the tested previous version; fresh synthetic previews show 1.14.

The ZIP contains the same installer, its checksum, instructions and license. English is the default README, with full descriptions in all 12 interface languages. Graphite appears first. Screenshots use synthetic demonstration data; an armed emergency state is an illustration, while the actual launch default is OFF.

Licensed under [PolyForm Noncommercial 1.0.0](LICENSE.md). Application sources are not published. Third-party runtime licenses remain in the installed runtime.


---

# VRAM GPU Desk 1.11

- Adds a separate opt-in emergency checkbox for GPU-heavy applications. It is **OFF at every launch**; the existing selected-application emergency option remains independent.
- The per-application GPU load threshold defaults to **20%**, configurable from **10–100%**. Only the threshold is saved. One attempt automatically turns the mode OFF, including cancellation or no eligible applications. Changing either threshold disarms it.
- Acts only after the selected GPU stays **strictly above the temperature-alert threshold for 10 seconds**, and an eligible application has met the GPU load threshold for **at least 3 seconds**.
- Uses read-only per-process GPU engine load, **not VRAM usage or memory-based heuristics**. Fresh measurements, unique physical GPU binding, process creation time, executable path and adapter LUID are checked. Native execution rechecks the exact instance and uses its validated handle.
- Unknown or stale data and protected, critical or unverifiable processes are skipped. Counter availability is required to arm the mode.
- **Useful or unwanted applications may be terminated, losing unsaved work.** Enable the option only when you accept this risk.
- Retains four instance-bound quick buttons, both themes, 12 languages, local history, UTF-8 CSV, temperature/idle cooling defaults and saved manual OFF choices. The protected installation model still uses one UAC prompt at installation.

## Checks and limits

Verification covers all **164 package files and 87 Java classes**, **40 isolated native checks**, **256 Java/settings/catalog checks**, and **673 UI checks across 48 language/theme/window-size cases**. The minimum window remains 1200×900 with the warning fully visible.

A read-only PDH check observed **710 valid GPU engine instances**, with **zero process-identity reads and no process termination**. Emergency behavior was tested with owned synthetic snapshots and fake RPC/actions. 

Screenshots contain synthetic demonstration data and simulated controller state. They illustrate the interface, not hardware operation or performance. Application source code and private diagnostic reports are not published. Download hashes are listed in [SHA256SUMS.txt](SHA256SUMS.txt).

## License

Free for noncommercial use under [PolyForm Noncommercial 1.0.0](LICENSE.md), subject to its terms and notice requirements. Commercial use requires separate permission. This is not an open-source license; application source code is not published. Third-party runtime licenses remain unchanged.
