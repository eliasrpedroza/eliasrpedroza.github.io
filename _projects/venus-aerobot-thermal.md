---
title: Venus Aerobot Thermal Control
context: NASA L'SPACE Mission Concept Academy · Team 27
summary: Thermal control subsystem for Venera Nova, a Venus aerobot mission concept, keeping the payload at 300 K through a 48-hour atmospheric descent from 70 to 50 km.
order: 5
featured: true
wide: true
thumb: /assets/img/projects/nasa/thumb.png
role: Thermal Engineer, owning the thermal control subsystem (TCS)
timeline: Jan – May 2025
team: ["Isabela Benavidez", "Rachel Brown", "Victor Chen", "Alaina Claudio", "Andrew Hoang", "Gregory Jabido", "Valerie Miranda", "Isaac Munoz", "Patrick Nguyen", "Tyree Nguyen", "Manahil Syeda"]
tags: [Thermal analysis, Heat transfer, Systems engineering, Siemens NX, Trade studies, Technical writing]
docs:
  - label: "Read the PDR paper (191 pp)"
    url: /assets/docs/venera-nova-pdr.pdf
  - label: "View the PDR slides"
    url: /assets/docs/venera-nova-pdr-slides.pdf
results:
  - "**Payload held at 300 K** in both extremes, 344.7 K (hot) and 225.8 K (cold), with ≈ 0 W net heat flow"
  - "**892 W rejected with zero power** in the hot case by a loop heat pipe and radiator"
  - "**15.86 kg subsystem mass**, under the 18 kg allocation; 147 W peak heater draw within a 165 W budget"
  - "**Co-authored and presented the 191-page Preliminary Design Review** to NASA evaluators"
---

## Mission

Venera Nova is a small, low-cost Discovery-class concept that sends a balloon-borne **aerobot** into Venus's atmosphere above Ovda Regio. It studies superrotation, the planet's induced magnetic field, and phosphine. Over a **48-hour descent from 70 km to 50 km**, the outside temperature swings from **225.8 K to 344.7 K**, while the payload's electronics and instruments need a steady **300 K**.

**Design constraints:** 300 ± 10 K internal, ≤ 18 kg, ≤ 165 W of active heating or cooling, ≤ 1 m² of radiator, ≤ $20 M.

## Heat Balance

Steady-state energy balances for both extremes, covering solar load, Venus albedo, atmospheric radiation, and convection on every face. Convection assumes the aerobot drifts with the winds, so the Reynolds number is ≈ 0, with CO₂ properties at each case's temperature.

<div class="demo-grid">
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/nasa/hot-case.png"><img class="demo-media" src="/assets/img/projects/nasa/hot-case.png" alt="Hot case heat flow map at 50 km"></a>
    <div class="demo-text">
    <h3>Hot Case · 50 km</h3>
    <ul>
      <li><strong>Inputs:</strong> 130.8 W solar (top face), 280.5 W albedo, 399.2 W atmospheric radiation</li>
      <li><strong>Rejection:</strong> 892 W carried by the loop heat pipe to the radiator, with no power input</li>
      <li><strong>Net:</strong> 891.5 W in vs. 892 W out → ≈ 0 W</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/nasa/cold-case.png"><img class="demo-media" src="/assets/img/projects/nasa/cold-case.png" alt="Cold case heat flow map at 70 km"></a>
    <div class="demo-text">
    <h3>Cold Case · 70 km</h3>
    <ul>
      <li><strong>Assumptions:</strong> night side (no solar load); albedo at 50% of the 50 km value</li>
      <li><strong>Make-up heat:</strong> 147 W from the flexible heater</li>
      <li><strong>Net:</strong> 366.6 W in vs. 366.4 W out → ≈ 0 W</li>
    </ul>
    </div>
  </div>
</div>

## Design

A mostly **passive** architecture keeps power draw low. The only active component is a heater that switches on when the payload drops 10 K below 300 K.

| Component | Function | Mass | TRL |
|---|---|---|---|
| Multi-layer insulation (5 faces) | Blocks radiative gain and loss | 3.5 kg | 7 |
| Z93 white coating | High-ε, low-α finish on the radiator face (ε = 0.92, α = 0.16) | ~0 | 7 |
| Al 6061 radiator | Rejects heat; 0.425 m² exposed area | 6.36 kg | 6 |
| Loop heat pipe | Capillary-driven, two-phase heat transport to the radiator | 4 kg | 6 |
| Polyimide thermofoil heater | Up to 147 W in the cold case | 3 g | 8 |
| **Total** | | **15.86 kg** | **6** |

<div class="demo-grid demo-grid--3">
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/nasa/payload.png"><img class="demo-media" src="/assets/img/projects/nasa/payload.png" alt="CAD of the 1 m³ payload with MLI and radiator panel"></a>
    <div class="demo-text">
    <h3>Payload Enclosure</h3>
    <ul>
      <li>1 m³ cube: MLI on five faces, Z93 radiator panel on the sixth</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/nasa/radiator.png"><img class="demo-media" src="/assets/img/projects/nasa/radiator.png" alt="CAD model of the Al 6061 radiator"></a>
    <div class="demo-text">
    <h3>Radiator</h3>
    <ul>
      <li>Z93-coated Al 6061; piped directly to the loop heat pipe</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/nasa/lhp.jpg"><img class="demo-media" src="/assets/img/projects/nasa/lhp.jpg" alt="Loop heat pipe phase-change cycle"></a>
    <div class="demo-text">
    <h3>Loop Heat Pipe</h3>
    <ul>
      <li>Two-phase, capillary-driven loop; moves 892 W with zero power <span class="credit">(diagram: Calyos)</span></li>
    </ul>
    </div>
  </div>
</div>

## Reliability

- **No hardware redundancy:** a second heat pipe, radiator, or heater would break the 18 kg limit, so flight-proven suppliers carry the risk instead
- **Software monitoring:** temperature sensors hold 300 ± 10 K, firing the heater below the band and triggering an emergency cooling mode if the heat pipe underperforms
- **Late scope change:** after NASA introduced a balloon-degradation issue, I re-verified that the thermal design still met every requirement

## Systems Engineering

- Coordinated thermal interfaces with the mechanical, power, CDH, and payload subsystems
- Carried the design through the MCR, SRR, MDR, and PDR reviews
