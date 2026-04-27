# Seam — Tolerance Allocation Tool

Seam is a Windows desktop application for mechanical tolerance allocation. It helps engineers allocate correct tolerances to dimensions in an assembly before drawings are issued — not after a stack-up failure surfaces in production.

Load a STEP assembly, detect contact surfaces automatically, define a tolerance accumulation direction (TAD), build a dimension chain, and allocate tolerances using ISO 2768 constraints and RSS-based allocation. Export the result as a self-contained HTML report.

**[Buy a License](https://dodo.pe/jtfbte4r2jt)** · **[Product Page](https://ahmed-essam-elrasoly.github.io/seam-landing/)**

---

## System Requirements

- Windows 10 or Windows 11 (64-bit)
- 8 GB RAM recommended
- ~1.6 GB free disk space for installation
- Internet connection required for first-time license activation only

---

## Installation

1. Download the installer (`Seam-Setup-0.1.0.exe`) from the [GitHub release](https://github.com/Ahmed-essam-elrasoly/seam/releases/tag/v0.1.0) or the product page.
2. Run the installer.
3. Windows will show a SmartScreen warning:

   > **"Windows protected your PC"**
   > Microsoft Defender SmartScreen prevented an unrecognized app from starting. Running this app might put your PC at risk.

   This appears because Seam does not yet carry an EV Authenticode signature. The application is safe. To proceed: click **More info**, then click **Run anyway**.

4. Follow the installer prompts. You can choose the installation directory.

---

## License Activation

1. Purchase a license at [https://dodo.pe/jtfbte4r2jt](https://dodo.pe/jtfbte4r2jt). Your license key will be emailed immediately after purchase.
2. Launch Seam. Enter your license key when prompted.
3. Activation requires an internet connection on first use only. After activation, Seam runs fully offline.
4. One license key activates one machine. A second activation on a different machine will be rejected.

---

## Quick Start

1. Drag a STEP file onto the viewer, or click **Open File** to browse.
2. Contact surface detection runs automatically. Contact faces are highlighted in the viewer.
3. Click **New TAD** and pick two points on the assembly to define the tolerance accumulation direction.
4. Add dimensions to build the chain. The chain must close (sum of projections ≈ TAD length) before allocation is enabled.
5. Set the TAD tolerance budget and click **Allocate**.
6. Review the result in the panel. Click **Export Report** to save an HTML report to disk.

---

## Known Limitations

- **30-day revalidation required.** Seam is not permanently offline. Approximately every 30 days, an internet connection is required to revalidate the license. A grace period of 3 days applies before the application restricts access. You will be notified in advance.
- **SmartScreen warning on install.** See installation instructions above. This is expected and not a security issue.
- **Installer size is approximately 1.5–1.6 GB.** This is due to the pythonocc geometry library and its dependencies being bundled for offline use.
- **Windows only.** macOS and Linux support is planned post-MVP.
- **One license key per machine.** A single license activates one machine only.
- **STEP AP214 format only.** Other STEP variants (AP203 from some older CAD tools) may fail to parse. If your file fails to load, re-export from your CAD tool using AP214 or AP203 with the "Save as" STEP option set to AP214.

---

## Open Source Attribution

### pythonocc-core

Seam uses [pythonocc-core](https://github.com/tpaviot/pythonocc-core) for STEP file parsing and 3D geometry processing.

Copyright (c) 2007-2023 Thomas Paviot (tpaviot@gmail.com) and contributors.

pythonocc-core is licensed under the [GNU Lesser General Public License v2.1 (LGPL)](https://www.gnu.org/licenses/old-licenses/lgpl-2.1.html). A copy of the LGPL v2.1 licence is included with this application as `COPYING.LESSER`.

### Open CASCADE Technology (OCCT)

pythonocc-core is built on [Open CASCADE Technology](https://dev.opencascade.org/), the underlying geometry kernel.

Copyright (c) 1999-2023 Open CASCADE SAS.

OCCT is licensed under the [Open CASCADE Technology Public License](https://dev.opencascade.org/doc/overview/html/license.html), which is based on LGPL v2.1 with an additional exception permitting use in proprietary software.

### Distribution

pythonocc-core and OCCT libraries are distributed as dynamically-loaded components (`OCC/Core/*.pyd` and `*.dll` files) in the application's resources directory. These files are unmodified and can be replaced with versions rebuilt from source.

---

## Support

- **GitHub Issues:** [https://github.com/Ahmed-essam-elrasoly/seam/issues](https://github.com/Ahmed-essam-elrasoly/seam/issues)
- **Email:** [a.essam.elrasoly@gmail.com](mailto:a.essam.elrasoly@gmail.com)

---

*Seam v0.1.0 · Windows-first · May 2026*