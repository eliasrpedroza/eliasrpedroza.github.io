---
title: RC Aircraft Landing Gear
context: Mechanical design course · Santa Clara University
summary: A retractable main landing gear for a Bobcat-52 RC aircraft, designed in SOLIDWORKS and checked with torque calculations and FEA.
order: 8
thumb: /assets/img/projects/rc/thumb.jpg
hero_side: true
hero_slides_ratio: 4 / 3
hero_slides:
  - src: /assets/img/projects/rc/stowed.jpg
    label: Stowed
    alt: Landing gear retracted flat, with the actuator, folded leg, wheel, and hatch servo
  - src: /assets/img/projects/rc/deployed.jpg
    label: Deployed
    alt: Landing gear extended, with the hatch swung open
  - src: /assets/img/projects/rc/wing.jpg
    label: On the wing
    alt: Landing gear mounted under the wing, extended
hero_caption: The actuator swings the leg down while a servo opens the wheel hatch.
timeline: Spring 2025
tags: [SOLIDWORKS, FEA, Motion study, Torque analysis]
results:
  - "**Retracting gear in CAD:** actuator-driven leg with a shock strut, plus a servo-driven hatch"
  - "**Drives sized:** 0.42 N·m to raise the leg in 2 s, 0.06 N·m for the hatch"
  - "**FEA:** fork peaked at 530 MPa vs. a 245 MPa yield, so it needs a stronger material"
  - "**$177 bill of materials:** printed PETG/TPU, aluminum, and steel"
---

## FEA

Peak von Mises stress (MPa) in the three load-bearing parts, modeled in 2017A aluminum (yield **245 MPa**). Values above yield are in bold.

| Part | Static load | Landing: 30 mph, 10 ft | Landing: 20 mph, 6 ft |
|---|---|---|---|
| Main gear shaft | 229 | **306** | **246** |
| Fork | **530** | **248** | 201 |
| Pivot | **434** | 189 | 98.8 |
