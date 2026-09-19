---
title: "IRIS: Integrated Reef Information System"
context: Senior Design · SCU Robotics Systems Lab
summary: An autonomous buoy–winch system that surfaces on a schedule to collect data from a submerged reef sensor network and upload it over cellular, with no divers required.
order: 1
featured: true
thumb: /assets/img/projects/iris/buoy-winch-dock.jpg
hero_video: /assets/video/iris-pool-test.mp4
hero_poster: /assets/video/iris-pool-test-poster.jpg
hero_portrait: true
hero_caption: Pool test. The ballasted buoy floats upright and returns to vertical after being disturbed.
role: "Buoy structure: mechanical design, CAD, and hydrostatic stability analysis"
timeline: 2025 – 2026 (3-quarter capstone)
team: ["Thatcher Steele-Maley", "Cooper McCarthy", "Zach Henderson", "Colin Friedel"]
tags: [SOLIDWORKS, Blue Robotics, Excel, Arduino, Marine]
results:
  - "**Self-righting buoy.** Metacentric height GM = +31.5 mm, confirmed upright in pool testing"
  - "**277 mm of stability margin.** Ballast sits 277 mm below the height where the buoy would capsize"
  - "**~120 mm of freeboard** above the waterline for the cellular antenna"
  - "**No dynamic shaft seals.** A magnetic coupling transmits winch torque through a sealed wall"
---

## System Overview

Reef sensor networks record data underwater, and today a diver has to go down to retrieve it. IRIS replaces that trip with a buoy stored below the surface. On a schedule, a winch raises it, it uploads the logged data over cellular, and it retracts to stay protected between cycles.

<figure>
  <img src="/assets/img/projects/iris/conops.jpg" alt="IRIS concept of operations">
  <figcaption>Concept of operations: sensors log data → the winch releases the buoy → it transmits to the cloud → it is reeled back down.</figcaption>
</figure>

<figure>
  <img src="/assets/img/projects/iris/system-block-diagram.png" alt="IRIS system block diagram">
  <figcaption>System architecture: power, data, and physical connections between the reef node, winch, buoy, and cloud.</figcaption>
</figure>

## Buoy

### Structure

- **Pressure vessel:** Blue Robotics 4" acrylic tube (114.3 mm OD × 300 mm) with a polycarbonate dome cap for the antenna
- **Frame:** twin aluminum T-slot rails clamped to the tube, carrying the tether mounts and shackles
- **Ballast:** modular 316 stainless weights that slide along the T-slots to tune stability
- **Electronics:** battery mounted low in the vessel; acoustic modem mounted externally below the bottom cap

<figure>
  <img src="/assets/img/projects/iris/buoy-winch-dock.jpg" alt="IRIS buoy and winch on a dock" style="max-height:560px;width:auto">
  <figcaption>Buoy (front) and tether winch before a water test.</figcaption>
</figure>

### Stability Analysis

The buoy must float upright so the antenna stays above water. Stability was checked with a full hydrostatic model built from a component-by-component inventory of mass and displaced volume.

<figure>
  <img src="/assets/img/projects/iris/stability-diagram.png" alt="Buoy stability diagram showing keel, center of gravity, center of buoyancy, and metacenter">
  <figcaption>When the buoy tilts, the center of buoyancy shifts to B′. Because the metacenter M sits above the center of gravity G, the buoyant force creates a righting moment.</figcaption>
</figure>

**Method**

1. Inventory every component: mass, displaced volume, and height above the keel K
2. Apply Archimedes' principle to find the waterline (2.84 L of seawater displaced)
3. Compute the center of gravity (KG) and center of buoyancy (KB) as weighted averages
4. Compute the metacentric radius BM = I<sub>wp</sub> / V<sub>sub</sub> from the waterplane geometry
5. **GM = KB + BM − KG**. The buoy is stable if GM > 0

| Quantity | Value |
|---|---|
| Total mass | 2.91 kg |
| Center of gravity, KG | 183.1 mm |
| Center of buoyancy, KB | 211.7 mm |
| Metacentric radius, BM | 2.9 mm |
| **Metacentric height, GM** | **31.5 mm (stable)** |

About **91% of the righting ability comes from the low ballast** (KB − KG = 28.5 mm). The slender tube's waterplane adds only 2.9 mm. A sensitivity sweep checked how far the ballast can move before the buoy becomes unstable:

{% include iris-gm-chart.html %}

The model is static and small-angle, which is appropriate here: the 114 mm buoy is far smaller than typical reef wavelengths, so it heaves with the waves instead of being slammed by them.

## Winch

*Team subsystem, shown for system context.*

- **Drive:** dual-servo winch with spur-gear speed reduction
- **Locking:** a ratchet-and-pawl holds the tether at depth without drawing power
- **Sealing:** a magnetic coupling transfers torque between the dry and wet sides, eliminating dynamic shaft seals, which are a common leak point

<figure>
  <img src="/assets/img/projects/iris/winch-block-diagram.png" alt="Winch block diagram with magnetic coupling between wet and dry sides">
  <figcaption>Winch drivetrain. The magnetic coupling separates the flooded tether drum from the sealed motor and battery.</figcaption>
</figure>

<div class="gallery">
  <figure><img src="/assets/img/projects/iris/pool-tests.jpg" alt="Pool testing"></figure>
  <figure><img src="/assets/img/projects/iris/winch-poc.jpg" alt="Winch proof of concept"></figure>
  <figure><img src="/assets/img/projects/iris/buoy-shell.jpg" alt="Early buoy shell concept"></figure>
</div>

## Results

The buoy passed its stability requirement by a wide margin: it floats upright with about 120 mm of freeboard for the antenna and rights itself in pool tests. The magnetically coupled winch drive removed the need for dynamic shaft seals.
