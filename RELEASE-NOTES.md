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

A read-only PDH check observed **710 valid GPU engine instances**, with **zero process-identity reads and no process termination**. Emergency behavior was tested with owned synthetic snapshots and fake RPC/actions. These checks performed **no actual process kills or GPU-setting writes**. They do not demonstrate sustained-load thermal performance or full production-installation hardware operation.

Screenshots contain synthetic demonstration data and simulated controller state. They illustrate the interface, not hardware operation or performance. Application source code and private diagnostic reports are not published. Download hashes are listed in [SHA256SUMS.txt](SHA256SUMS.txt).

## License

Free for noncommercial use under [PolyForm Noncommercial 1.0.0](LICENSE.md), subject to its terms and notice requirements. Commercial use requires separate permission. This is not an open-source license; application source code is not published. Third-party runtime licenses remain unchanged.
