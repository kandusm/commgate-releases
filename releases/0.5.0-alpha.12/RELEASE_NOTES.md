**v0.5.0-alpha.12: version 1.1 of the engine's licence.** A pre-release. Install and upgrade as before
(INSTALL.md §1): an earlier alpha upgrades in place, keeping paired projects, devices and the engine
ID. Update the gateway first, then all eight drivers.

**New:**
* **The CommGate Engine License Agreement, version 1.1** (`EULA.txt`), with counsel's amendments. It replaces version
  1.0 for this release and every hardware unit flashed from its image; releases already published keep version 1.0.
  Version 1.1 widens the licence to the Software's intended interoperability and automation functions, including
  personal and commercial installations; lets an installer or dealer deliver the Software to a customer as part of a
  CommGate installation and charge for hardware and services; keeps hardware's own written warranty separate; and adds
  a safety-critical applications clause (section 10) and a severability clause (section 11). Read the full text in
  `EULA.txt`: this summary is not part of it. It ships where version 1.0 did: the root of the engine tarballs,
  `/usr/share/doc/commgate/` on every install and hardware unit, and with the release, next to THIRD_PARTY_NOTICES.

**Fixed:**
* About one in 256 of the HTTPS certificates the engine makes for itself had a serial number encoded in a way that
  certificate parsers reject. The engine then stopped at startup and made a new certificate when systemd restarted it,
  so units recovered by themselves, but the first start failed. Every certificate is now encoded correctly.

**Drivers.** Composer version 50012. The drivers' code and documentation are unchanged from alpha.11 (50011); the
number rises because every release's drivers carry its version. Update with all eight files.

**Qualified:** engine 108/108 and drivers 232 unit + 42/42 integration on macOS and Ubuntu; the
shared checks pass in fresh Ubuntu 24.04 and Debian 12 LXD containers (with a re-run, a reboot and the migration from
a pre-v0.4 host); the release build checks the tarballs carry EULA.txt (version 1.1) and THIRD_PARTY_NOTICES; the
hardware image passes its boot test in the factory's order (the card on the boot partition after first boot,
`commgate check` failing on it, 0 failures once it is deleted, and `commgate update` not putting it back), with its
package list identical to alpha.11's (633 packages); 2000 certificates in a row parse. A hardware unit (Raspberry Pi
5) updated in place through the support shell passes every check (0 failures), its Control4 project reconnected
encrypted with no re-pair, and its 17 devices came back.

**Files:** the hardware image for Raspberry Pi 4/5, the engine for 64-bit Linux (arm64 and x64), the eight Control4 drivers with their installation guide (zip), and INSTALL.md. Also the corresponding source of the image's GPL and LGPL packages (the source .tar file; see the source offer). The engine's licence (EULA.txt), the image's package list, the open-source notices and the GPL source offer are linked below.

*CommGate is not affiliated with, endorsed by, or certified by the Connectivity Standards Alliance. Matter is a
trademark of the Connectivity Standards Alliance.*
