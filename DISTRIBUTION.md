# Distribution

This repository publishes compiled Windows x64 installers and documentation. Application source code, source archives, private diagnostic reports, user settings and history are not included.

The 1.11 EXE includes a Java runtime and local Windows helpers. The installer ZIP contains the same sealed installer plus its checksum, instructions and LICENSE.md; it is not a portable installation. Installation uses a fixed protected Program Files directory and requires the currently signed-in split-token administrator. The application and installer are not signed with a personal publisher certificate.

Java runtime third-party license notices are retained under runtime/legal in the installed application. NVIDIA driver libraries are not bundled or downloaded: the installed system library must pass the application's offline signature, path and API checks.

SHA256SUMS.txt covers downloadable packages. Published images use synthetic demonstration data and simulated controller state. They illustrate the interface and do not demonstrate hardware operation or thermal performance.

## License

Free for noncommercial use under [PolyForm Noncommercial 1.0.0](LICENSE.md), subject to its terms and notice requirements. Commercial use requires separate permission. This is not an open-source license; application source code is not published. Third-party runtime licenses remain unchanged.
