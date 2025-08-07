
# Mechanical Fabrication and Documentation Standards

## Purpose

This document defines the official company standard for managing, documenting, and controlling mechanical designs used in fabrication — including **weldments**, **CNC-routed parts**, and **precision machined components**.

These standards apply to:

- Internal fab teams producing parts in-house
- Mechanical engineers creating Fusion 360 models
- External vendors building off our documentation
- Anyone responsible for maintaining product structure and mechanical fit

The objective is to ensure that all mechanical assets are:

- Controlled through versioned models and drawings
- Built to specification with traceable materials and tolerances
- Reviewed and approved via a formal change process
- Ready for knowledge transfer, scale, and investor evaluation

---

## Why This Matters

Mechanical assemblies are often central to our products — they carry batteries, sensors, housings, or structures for critical systems. Errors in this domain are costly:

- A bad weldment or misaligned CNC part can stall an entire build
- Poorly documented parts cannot be reproduced or modified safely
- Uncontrolled design changes lead to confusion, scrap, or rework
- Knowledge silos cause downtime when key people are unavailable
- Investors or auditors may flag poor documentation as a risk

This standard protects against those risks. It ensures that each design can be fabricated, transferred, revised, and scaled with confidence — even when teams grow, shift, or hand off responsibilities.

---

## Who This Applies To

- Mechanical engineers and designers using Fusion 360
- CNC programmers and machine operators
- Fabricators and welders building structural assemblies
- Product and operations managers responsible for handoffs or scalability
- Any contributor to physical product development

---

## Key Policies

| Requirement | Description |
|-------------|-------------|
| **Control Model** | Only one official model per part/assembly (Fusion 360). Editable by a single qualified owner. |
| **ECR/ECO Required** | All design changes must be proposed through an Engineering Change Request (ECR) and implemented via Engineering Change Order (ECO). |
| **Drawing Standards** | All machined/CNC/welded parts must include full technical drawings with dimensions, tolerances, GD&T, materials, and finish notes. |
| **Revision Control** | Every part and assembly must carry a revision ID (Rev A, B, C...) tracked in a change log. |
| **Build Packages** | Complete fabrication packages are required for all assemblies, including cut files, weld callouts, and setup notes. |
| **Manufacturability** | Drawings and models must reflect real-world manufacturability — no missing details, impossible fits, or tribal knowledge. |

---

## Folder & File Structure Example

```

/assembly-name/
├── README.md
├── control-model/
│   └── welded-assembly.f3z
├── drawings/
│   ├── base-plate.pdf
│   ├── gusset.dxf
│   └── weldment-assy.pdf
├── cut-files/
│   ├── sheetmetal-profile.dxf
│   └── router-toolpaths.nc
├── cam-programs/
│   └── mill-op1-plate.f3d
├── fabrication-notes/
│   ├── weld-sequence.md
│   ├── inspection-checklist.md
│   └── critical-fits.md
├── revision-history/
│   └── rev-log.md
├── change-management/
│   ├── ECR-004.md
│   ├── ECO-004.md
│   └── approvals/

````

---

## README.md Template for Mechanical Assembly

```markdown
# Battery Rack Weldment (Rev C)

## Overview
Welded steel frame supporting two battery enclosures in a floor-mounted configuration for Vehicle Integration Bay 3.

## Control Model
- File: `/control-model/batt-rack.f3z`
- Owner: Marco Rivera (Mechanical Design)
- Last controlled update: ECO-004, Aug 2025

## Assembly Summary
- Welded from laser-cut mild steel plate and tubing
- Locating pins interface with robot lift arms
- Precision machined slots for bolted ground lugs

## Fabrication
- Process: MIG weld
- Material:
  - Main tubing: 2"x2"x.125" A36 steel
  - Plate: 0.25" HRPO mild steel
- Hardware:
  - M12 flange bolts (Grade 10.9, torque 80 Nm)
  - All hardware shown in exploded drawing `/drawings/weldment-assy.pdf`

## CNC and Machining
- Plate profile cut on ShopSabre CNC router
- CAM toolpath: `/cut-files/base-plate.nc`
- Holes and slots: Precision drilled on VF-2 CNC mill using Op1 program

## Welding Details
- Start at base corners, square with jig #17
- Heat distortion check after diagonal welds
- Weld sequence and inspection steps in `/fabrication-notes/weld-sequence.md`

## Inspection & Fit
- Check cross-diagonal within ±1.5mm
- Bolt hole position tolerance: ±0.25mm
- Confirm flatness on top deck (< 2mm sag)

## Revision History
- Rev A – Initial release
- Rev B – Hole pattern updated for V3 battery
- Rev C – Added mounting tab and adjusted weld order (see ECO-004)

## Safety Notes
- Designed for 300kg load (2x battery modules)
- Verified weld strength via FEA simulation (included in docs/ folder)
- Sharp edge chamfer callouts required for safe handling

## Contact
- Mechanical Owner: Marco Rivera – marco.rivera@company.com
- Fabrication Lead: Alicia Zhou – alicia.zhou@company.com
- ECO Coordinator: eng.ops@company.com
````

---

## Change Management Process (ECR/ECO)

**No edits** to the control model may be made outside of this process:

1. **ECR (Engineering Change Request)**

   * Proposes a change (e.g., material switch, tolerance update, new cutout)
   * Must include justification and supporting documentation (screenshots, issue reports, test results)
   * Submitted to engineering operations or a designated approver group

2. **ECO (Engineering Change Order)**

   * Formal approval of the ECR
   * Triggers update to control model by authorized editor
   * Updated drawings, CAM programs, and build files are generated
   * Change is logged in `/revision-history/rev-log.md`

3. **Communication**

   * Updated revision released to fabrication team
   * Superseded files archived or marked obsolete

**Unauthorized edits to Fusion models are not permitted under this policy.**

---

## Drawing Requirements

All drawings must include:

* Standard title block with part name, drawing number, and revision
* Units (metric or imperial) consistently specified
* Critical dimensions and tolerances
* Datum references and geometric tolerancing (GD\&T) for machined fits
* Surface finish or coating notes (e.g., powder coat, anodize)
* Welding symbols (where applicable)
* Sheet scale and drawing scale

Use Fusion 360 drawing exports with proper PDF naming (e.g., `bracket-revB.pdf`).

---

## Fabrication Packages Must Include:

* Cut files (DXF, NC, or other CNC-ready formats)
* Technical drawings with full dimensions
* CAM files or toolpaths (if internal machining)
* Welding sequence or jig notes
* Assembly order (for multi-stage builds)
* Inspection checklist (as Markdown or PDF)
* Material callouts (grade, spec, finish)

---

## Audit, Handoff, and Investor Readiness

Mechanical documentation is subject to:

* Internal handoffs (new hires, shift transitions, team changes)
* External manufacturing (vendors, outsourcing, scaling)
* Technical audits (compliance, liability, certification)
* Investor diligence (evaluating ability to scale or replicate)

Each assembly must be documented well enough that a qualified fabricator could produce it without direct knowledge transfer.

This includes revision tracking, access control, test results, and safety/fit notes.

---

## Contact

For help with mechanical documentation or change control:

**Mechanical Engineering Operations**
**[mech.ops@company.com](mailto:mech.ops@company.com)**

---

## License

This documentation standard is internal IP of \[Your Company Name]. Do not redistribute or publish outside the organization.
