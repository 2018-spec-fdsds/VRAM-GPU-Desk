# Activation privacy and local data

This document describes VRAM GPU Desk 1.24. English is the primary language.

## Local device identity

Offline activation reads local device identity through Windows interfaces: a valid SMBIOS system UUID is preferred, with validated mainboard information and a Windows installation identifier fallback when necessary. A GPU replacement alone is not used as a licence identity change. Invalid or placeholder hardware values are not invented into a new random identity on each launch.

The application derives an opaque 20-character request code from that identity. The request is a stable device-derived identifier, not an anonymous token. It does not expose the original UUID, mainboard serial or Windows identifier as plain text. The activation flow has no designed-in hardware-identifier upload or activation-server request.

You decide whether and how to share the request with the application owner to obtain a response. Saving the request writes a UTF-8 TXT file at the location you choose. It contains the request code; it does not collect prompts, model inputs, images, videos or application document contents.

## Local licensing state

The protected licensing component retains the first supported launch time, a nondecreasing time high-water mark, the device request code and activation status. The fixed local state folder is `%PROGRAMDATA%\VRAMGPUDesk-License`; its state is protected with Windows DPAPI and restrictive System/Administrators permissions. Normal application operations use a typed local channel to the dedicated licensing task, not an arbitrary file-writing or GPU-control endpoint.

Setup creates the protected folder and task but does not initialize the 60-day anchor. The first supported application query does. Ordinary updates and uninstall/reinstall preserve this state, so updating or reinstalling does not start another 60-day period. Hardware identity changes invalidate activation without resetting the original trial anchor. Corrupt state is not silently rewritten as a fresh trial.

The owner key generator and owner master-key file are held separately and are not distributed. A compact 20-character offline response requires an application-side verifier; reverse engineering or a local administrator can bypass or alter an offline application. DPAPI, time high-water checks and filesystem permissions are not a claim of absolute tamper resistance.

## Functionality and reminders

After 60 days, all features remain available. The change is a localized activation reminder at least hourly while the program runs. A valid response tied to the current device identity stops those reminders. The application does not intentionally disable GPU temperature control, cooling, monitoring or process actions because the period expired.

A reminder can be topmost over ordinary Windows windows; it cannot override the protected Windows/UAC desktop or guarantee priority over every other system window.

## Other application data

Preferences, per-GPU settings, quick-button bindings, history, local application logs and exported CSV files retain their existing local storage and behavior. Their contents are not submitted as part of activation. Request and response codes are not intended to contain those records or user content.

The application does not include a designed-in telemetry uploader, online activation service, cloud inference service, automatic updater or runtime model downloader. This describes the application and activation flow; it is not a guarantee of OS-wide network isolation or of third-party Windows/driver behavior.

Use is subject to [PolyForm Noncommercial 1.0.0](LICENSE.md). Commercial use requires separate permission; activation does not silently replace those licence terms.
