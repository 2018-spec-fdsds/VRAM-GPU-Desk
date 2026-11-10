# VRAM GPU Desk 1.6

Driver-independent NVML admission, clear UAC startup/failure feedback, refreshed GPU icon and one Start-menu shortcut. Existing settings and controller policies are preserved.

The system driver library is checked offline through Windows trust validation and its verified NVIDIA publisher. There is no list of allowed driver versions or DLL hashes. Available hardware and API support are still required; this is not a promise of universal GPU support.

Validation: live sensors; elevated read-only power/fan driver admission; 12 UI languages, two themes, UTF-8 CSV and settings/tray tests; CPU planners 33/440/5709 checks. No actual hardware-setting writes or sustained GPU load test were performed for this release. The installer is unsigned.

Compiled binaries only. No application sources, user settings, private process lists or user media are included. Screenshots contain synthetic demonstration data.
