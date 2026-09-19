---
title: RC Aircraft Landing Gear
context: Mechanical design analysis
summary: Kinematic and FEA validation of a retractable rear landing gear for a Bobcat-52 RC aircraft.
order: 8
featured: false
thumb: /assets/img/projects/rc/fea.png
hero_image: /assets/img/projects/rc/exploded.jpg
tags: [SOLIDWORKS, FEA, Kinematics]
results:
  - "**Found components exceeding yield** under aggressive landing cases (up to 530 MPa in the fork)"
  - "**Guided material selection** and redesign priorities"
---

## Approach

- Assembled the system CAD and produced exploded views
- **Kinematic analysis** to estimate the actuator torque needed to retract the gear
- **FEA** of the critical components (main gear shaft, fork, and pivot) under landing and static loads

<figure><img src="/assets/img/projects/rc/fea.png" alt="FEA stress results for main gear shaft, right fork, and pivot"><figcaption>Peak von Mises stress: 229 MPa (shaft), 530 MPa (fork), 434 MPa (pivot).</figcaption></figure>

## Outcome

Several parts exceeded their yield stress in the aggressive landing cases. Those results set the material choices and redesign priorities for the next iteration.
