**v0.5.0-alpha.10: licensing through DriverCentral, encrypted drivers, and an exact subscription interval.** A
pre-release. Install and upgrade as before (INSTALL.md §1): an earlier alpha upgrades in place, keeping
paired projects, devices and the engine ID. Update the gateway first, then all eight drivers.

**New:**
* **Licensing through DriverCentral.** One license covers all eight drivers in a project. The project needs
  DriverCentral's free *DriverCentral Cloud* driver, linked on drivercentral.io; licenses, the 7-day trial and showroom
  licenses are managed there, and nothing is typed into the parent. The parent's new **License** property says where
  things stand (*licensed*, *trial, N hours left*, or *not licensed* with what to do) and DriverCentral's **Cloud
  Status** shows its own text. Without a license the parent refuses device commands (each device's Last Error says why),
  stops passing device updates to Control4 and shows the devices offline; pairing, discovery, adding devices, properties
  and the gateway connection keep working and nothing is unpaired. Activating restores control within seconds, with no
  restart: after assigning a license on drivercentral.io, run **Check Drivers** on the DriverCentral Cloud driver (its
  Properties tab, **Driver Actions** list) so the project picks it up at once. A project that has been licensed gets **72 hours** when its license check starts failing
  (the Cloud driver removed or offline, a license unlinked): control keeps working and **License** counts down; a trial
  gets no grace. **Forget License History** (action) ends a grace at once, for testing. Leave the new **Automatic
  Updates** property Off: the eight drivers update together.
* **The drivers are encrypted** (Control4's DriverWorks encryption). The Lua tab still shows their output but no longer
  takes commands: run diagnostics such as **TLS Self-Test** from the Actions tab.

**Fixed:**
* The gateway asked each device for a subscription interval up to 10 s longer than configured (the Matter stack added
  random jitter to it), so a silent device could take that much longer to show offline. It now asks for exactly the
  configured ceiling; the device may still add its own few seconds (in tests a device that stops is flagged offline
  after 32 s instead of 37 s with a 20 s ceiling).

**Drivers.** Composer version 50010. There is no alpha.9 release: its number, 50009, went to the bench candidates
(0.5.0-alpha.9-candidate.N), and this release installs over them. The parent changed (licensing); the children changed
only by being encrypted; update with all eight files.

**Qualified:** engine 105/105 and drivers 232 unit + 42/42 integration on a Mac and on Ubuntu (mcc-auto01); the shared
checks pass in fresh Ubuntu 24.04 and Debian 12 LXD containers (with the event port's TLS and the migration from a
pre-v0.4 host); the hardware image passes its boot test (first boot, then `commgate update` through the support shell),
and its package list matches the pinned Raspberry Pi OS base exactly (633 packages, nothing added or removed); a
hardware unit (Raspberry Pi 5) updated in place through the support shell passes the shared checks (0 failures), its
Control4 project reconnecting encrypted with no re-pair. The licensing was verified live on a Control4 EA-5 (OS 3.4.1)
with real devices and DriverCentral (the drivers of this release as candidate 0.5.0-alpha.9-candidate.2): the trial
counting down over 7 days, licensing from the portal, the block on natural trial expiry (held ~36 h, connection
encrypted throughout), recovery without a restart or re-pair, the 72-hour grace with control working, Forget License
History, and re-licensing; TLS, pairing and control both ways unchanged.

**Open (not blocking this pre-release):** the controller-side TLS answers are confirmed on the EA-5 (OS 3.4.1); OS 3.3
and an X4 are pending hardware access.

**Files:** the hardware image for Raspberry Pi 4/5, the engine for 64-bit Linux (arm64 and x64), the eight Control4 drivers with their installation guide (zip), and INSTALL.md. Also the corresponding source of the image's GPL and LGPL packages (the source .tar files; see the source offer). The image's package list, the open-source notices and the GPL source offer are linked below.

*CommGate is not affiliated with, endorsed by, or certified by the Connectivity Standards Alliance. Matter is a
trademark of the Connectivity Standards Alliance.*
