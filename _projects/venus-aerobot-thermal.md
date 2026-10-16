---
title: Venus Aerobot Thermal Control
context: NASA L'SPACE Mission Concept Academy · Team 27
summary: Thermal control subsystem for Venera Nova, a Venus aerobot mission concept, keeping the payload near room temperature (300 K / 80 °F) through a 48-hour descent through Venus's atmosphere.
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
  - "**Payload held at 300 K (80 °F)** while outside temperatures ranged from −53 °F to 161 °F, with ≈ 0 W net heat flow"
  - "**892 W rejected with zero power** in the hot case by a loop heat pipe and radiator"
  - "**15.86 kg subsystem mass**, under the 18 kg allocation; 147 W peak heater draw within a 165 W budget"
  - "**Co-authored and presented the 191-page Preliminary Design Review** to NASA evaluators"
---

## Mission

Venera Nova is a low-cost, Discovery-class concept that would study how Venus's surface and interior interact with its atmosphere: its superrotation, its lack of an intrinsic magnetic field, and the potential for life in its upper clouds. A balloon-borne **aerobot** carries a 1 m³ instrument payload on a **48-hour descent from 70 km to 50 km**, within a 45 kg system mass and a 167.2 W power limit.

Over that descent the outside atmosphere swings from **225.8 K (−53 °F) to 344.7 K (161 °F)**, while the payload's electronics have to stay near room temperature: **300 K (80 °F)**.

**Design constraints:** 300 ± 10 K (80 ± 18 °F) internal, ≤ 18 kg, ≤ 165 W of active heating or cooling, ≤ 1 m² of radiator, ≤ $20 M.

## Heat Balance

I designed the system around steady-state energy balances at the two extremes. Each one adds up every heat path into and out of the cube, then solves for the cooling or heating needed to bring the net to zero:

- **Solar:** 1367 W/m² scaled to Venus's orbit (0.723 AU), on the top face only
- **Reflected sunlight (albedo):** Venus's 0.75 albedo, with view factors of 1 for the bottom face and 0.3 for the sides
- **Radiation:** Stefan–Boltzmann exchange between every face and the surrounding atmosphere, using the MLI emissivity on five faces and Z93 on the sixth
- **Convection:** the aerobot drifts with the wind, so relative velocity ≈ 0 (Nu ≈ 0.3), with CO₂ conductivity evaluated at each case's temperature

<div class="demo-grid">
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/nasa/hot-case.png"><img class="demo-media" src="/assets/img/projects/nasa/hot-case.png" alt="Hot case heat flow map at 50 km"></a>
    <div class="demo-text">
    <h3>Hot Case · 50 km · 344.7 K (161 °F)</h3>
    <ul>
      <li><strong>Heat in:</strong> 130.8 W solar, 280.5 W reflected sunlight (albedo), and 399.2 W from the hot atmosphere</li>
      <li><strong>Heat out:</strong> 892 W carried to the radiator by the loop heat pipe, using no power</li>
      <li><strong>Net:</strong> 891.5 W in vs. 892 W out → ≈ 0 W</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/nasa/cold-case.png"><img class="demo-media" src="/assets/img/projects/nasa/cold-case.png" alt="Cold case heat flow map at 70 km"></a>
    <div class="demo-text">
    <h3>Cold Case · 70 km · 225.8 K (−53 °F)</h3>
    <ul>
      <li><strong>Conditions:</strong> night side, so no direct sunlight; albedo halved in the thinner cloud layer</li>
      <li><strong>Heat added:</strong> 147 W from the thermofoil heater</li>
      <li><strong>Net:</strong> 366.6 W in vs. 366.4 W out → ≈ 0 W</li>
    </ul>
    </div>
  </div>
</div>

## Design

A mostly **passive** design keeps power use low. The heater is the only part that draws power, and it switches on only when the payload drops 10 K (18 °F) below target.

| Component | Function | Mass | TRL |
|---|---|---|---|
| Multi-layer insulation (5 faces) | Blocks heat gain and loss | 3.5 kg | 7 |
| Z93 white coating | Reflects sunlight, emits heat; on the radiator face | ~0 | 7 |
| Al 6061 radiator | Dumps heat to the atmosphere; 0.425 m² | 6.36 kg | 6 |
| Loop heat pipe | Carries heat from the electronics to the radiator, with no power | 4 kg | 6 |
| Thermofoil heater | Adds up to 147 W in the cold case | 3 g | 8 |
| **Total** | | **15.86 kg** | **6** |

<div class="demo-grid">
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/nasa/payload.png"><img class="demo-media" src="/assets/img/projects/nasa/payload.png" alt="CAD of the 1 m³ payload with MLI and radiator panel"></a>
    <div class="demo-text">
    <h3>Payload Enclosure</h3>
    <ul>
      <li>1 m³ cube: insulation on five faces, Z93-coated radiator panel on the sixth</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/nasa/radiator.png"><img class="demo-media" src="/assets/img/projects/nasa/radiator.png" alt="CAD model of the Al 6061 radiator"></a>
    <div class="demo-text">
    <h3>Radiator</h3>
    <ul>
      <li>Z93-coated Al 6061 panel, piped directly to the loop heat pipe</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/nasa/lhp.jpg"><img class="demo-media" src="/assets/img/projects/nasa/lhp.jpg" alt="Loop heat pipe phase-change cycle"></a>
    <div class="demo-text">
    <h3>Loop Heat Pipe</h3>
    <ul>
      <li>Fluid boils off at the electronics, condenses at the radiator, and wicks back, moving 892 W with zero power <span class="credit">(diagram: Calyos)</span></li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/nasa/heater.jpg"><img class="demo-media" src="/assets/img/projects/nasa/heater.jpg" alt="Minco HAP6948-1 thermofoil heater drawing"></a>
    <div class="demo-text">
    <h3>Thermofoil Heater</h3>
    <ul>
      <li>Minco HAP6948-1 flexible polyimide heater, bonded to the internal chassis wall so heat spreads by conduction</li>
      <li>Rated to 170.9 W; capped at 162.7 W by the power budget, against a 147 W need <span class="credit">(drawing: Minco)</span></li>
    </ul>
    </div>
  </div>
</div>

## Reliability

- **No hardware redundancy:** a second heat pipe, radiator, or heater would break the 18 kg limit, so flight-proven suppliers carry the risk instead
- **Software monitoring:** temperature sensors hold 300 ± 10 K, turning on the heater below the band and triggering an emergency cooling mode if the heat pipe underperforms
- **Late scope change:** after NASA introduced a balloon-degradation issue, I re-verified that the thermal design still met every requirement

## Systems Engineering

- Coordinated thermal interfaces with the mechanical, power, CDH, and payload subsystems
- Carried the design through the MCR, SRR, MDR, and PDR reviews
