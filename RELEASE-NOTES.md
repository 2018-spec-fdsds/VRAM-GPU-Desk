# VRAM GPU Desk — release notes

## 1.15

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
