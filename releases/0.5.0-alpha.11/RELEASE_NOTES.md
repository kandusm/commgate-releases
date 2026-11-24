**v0.5.0-alpha.11: the engine's licence, and the factory checks for sellable hardware units.** A pre-release. Install
and upgrade as before (INSTALL.md §1): an earlier alpha upgrades in place, keeping paired projects,
devices and the engine ID. Update the gateway first, then all eight drivers.

**New:**
* **The engine's licence.** The engine and the hardware image are licensed under the CommGate Engine License Agreement
  (`EULA.txt`): free to use, with the gateway's open-source components under their own licences. It ships at the root
  of the engine tarballs, in `/usr/share/doc/commgate/` on every install and hardware unit, and with the release, next
  to THIRD_PARTY_NOTICES. The Control4 drivers are licensed separately through DriverCentral.
* **`commgate check` fails while the factory card is on the boot partition.** A hardware unit's first boot writes its
  card (with the pairing code) to the SD card's boot partition for printing; the factory prints it and deletes the
  folder. The check now fails, with *factory card still on /boot — print and delete it before shipping (factory
  procedure step 3)*, while the folder or a copy of it (such as one in a `.Trashes` folder) is still there. If a unit
  you set up yourself fails this, delete `commgate-label` from the card's boot volume (on a Mac: `rm -rf /Volumes/bootfs/commgate-label`; the Finder's
  delete keeps a copy on the card).
* **The support login gains `vcgencmd`** (the Pi's temperature, clocks and throttling) and `sleep`, for the factory's
  PoE qualification.
* **What goes over the internet** is now in INSTALL.md §2.4 and the driver's documentation: the gateway sends no
  telemetry to CommVergent; it downloads public device certificates; a hardware gateway's OS syncs its clock and
  checks package lists; DriverCentral's licensing client reports its own errors to DriverCentral's server.

**Fixed:**
* An update on a hardware unit wrote the card, with the pairing code, back to the boot partition after the factory
  had deleted it. The card now goes there only at first boot. A unit updated with an earlier release may have the folder
  back: `commgate check` says so; delete it as above.

**Drivers.** Composer version 50011. Only the documentation changed (documentation.html, INSTALL.md); update with all
eight files.

**Qualified:** engine 106/106 and drivers 232 unit + 42/42 integration on macOS and Ubuntu; the
shared checks pass in fresh Ubuntu 24.04 and Debian 12 LXD containers, with the new licence checks (with a re-run,
a reboot and the migration from a pre-v0.4 host); the release build refuses a tarball without EULA.txt or
THIRD_PARTY_NOTICES; the hardware image passes its boot test, now in the factory's order: first boot writes the card
to the boot partition, `commgate check` fails on it with the factory message, the folder is deleted, the checks pass
(0 failures), and `commgate update` through the support shell doesn't put it back; its package list matches the
pinned Raspberry Pi OS base exactly (633 packages, as in alpha.10). A hardware unit (Raspberry Pi 5) updated in place
through the support shell passes every check but the new card check, as intended: its alpha.10 update had written the
card back (the bug fixed here) and the alpha.11 update left it untouched. Its Control4 project reconnected encrypted
with no re-pair, and `vcgencmd` works from the support login (the PoE procedure's readouts).

**Files:** the hardware image for Raspberry Pi 4/5, the engine for 64-bit Linux (arm64 and x64), the eight Control4 drivers with their installation guide (zip), and INSTALL.md. Also the corresponding source of the image's GPL and LGPL packages (the source .tar file; see the source offer). The engine's licence (EULA.txt), the image's package list, the open-source notices and the GPL source offer are linked below.

*CommGate is not affiliated with, endorsed by, or certified by the Connectivity Standards Alliance. Matter is a
trademark of the Connectivity Standards Alliance.*
