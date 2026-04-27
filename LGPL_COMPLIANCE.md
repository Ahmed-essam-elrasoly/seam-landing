# LGPL Compliance — pythonocc-core

**Date:** April 23, 2026
**Decision:** Path A — dynamic linking argument, documented.

---

## Library Details

| Field        | Value                                              |
|--------------|----------------------------------------------------|
| Library      | pythonocc-core                                     |
| Licence      | GNU Lesser General Public License v2.1 (LGPL)     |
| Version      | 7.9.3                                              |
| Source       | https://github.com/tpaviot/pythonocc-core          |
| Licence text | https://www.gnu.org/licenses/old-licenses/lgpl-2.1.html |

---

## How pythonocc-core Is Used

Seam uses pythonocc-core for STEP file parsing, BRep tessellation,
and geometry queries (face normals, edge endpoints, contact detection,
point projection). Seam's own code (bridge.py, allocator.py, detector.py,
and related modules) imports pythonocc dir      ectly via standard Python imports.
Seam does not modify pythonocc-core source code.

---

## Distribution Structure

bridge.dist contains:
  bridge.exe              ← Seam's compiled code only (Nuitka standalone)
  OCC/Core/*.pyd          ← pythonocc extension modules (unmodified, from source package)
  OCC/Core/*.py           ← pythonocc Python wrappers (unmodified)
  *.dll                   ← OpenCASCADE + support libraries (TK*, freeimage, freetype, tbb*)

All OCC and OCCT files are copied unmodified from the pythonocc-core conda package.
bridge.exe contains only Seam's compiled code — no OCC source is compiled into it.
---

## LGPL Obligations and How They Are Met

### 1. User Can Replace the Library

The pythonocc extension modules (`OCC/Core/*.pyd`) and the underlying
OpenCASCADE libraries (`tk*.dll`) are present as accessible, separate
files in the application's resources directory after installation.

A user may replace these files with versions rebuilt from the
pythonocc-core source code (https://github.com/tpaviot/pythonocc-core)
without any modification to Seam's own compiled code.

The `--nofollow-import-to=OCC` Nuitka flag is set intentionally to
ensure OCC modules remain as separate .pyd files and are never inlined
into bridge.exe. This flag must be preserved in all future builds.

### 2. Attribution

pythonocc-core is credited in README.md with its licence type, licence
link, and source repository link, as required by LGPL v2.1.

### 3. No Anti-Reverse-Engineering Measures

No technical measures are applied to the `.pyd` or `.dll` files that
would prevent modification, debugging, or replacement of pythonocc-core
or the underlying OpenCASCADE libraries.

---

## Residual Risk Acknowledgement

The application of LGPL v2.1 to Python extension modules has no
definitive case law. This compliance position is a reasoned good-faith
effort based on the dynamic linking exemption — the established basis
for commercial use of LGPL libraries.

This document represents a conscious risk decision, not a legal guarantee.
The practical enforcement risk at indie scale ($50–100 pricing, small
initial user base) is assessed as low. If Seam's commercial scale
increases materially, a formal written legal opinion from an IP solicitor
should be obtained.

---

## Open Items

- [ ] Confirm exact post-install path after Day 17 Sandbox test and
      update the placeholder above.

---

*Filed: April 23, 2026*
*Author: Ahmed (Russty)*