---
title: "IRIS: Integrated Reef Information System"
context: Senior Design · SCU Robotic Systems Lab
summary: A buoy–winch system that waits safely below the surface, rises on a schedule to send reef sensor data over cellular, then retracts, with no divers needed. I designed the buoy that has to surface, stay upright, and keep its antenna above the water.
order: 1
featured: true
wide: true
thumb: /assets/img/projects/iris/buoy-winch-dock.jpg
hero_video: /assets/video/iris-swaying.mp4
hero_poster: /assets/video/iris-swaying.jpg
hero_portrait: true
hero_caption: Bay deployment in Foster City. The buoy rides the wind chop and stays upright, with its dome and cellular antenna above the surface.
role: "Buoy structure and surface stability: enclosure selection, structural design and materials, hydrostatic analysis, and water testing"
timeline: Jun 2025 – Jun 2026 (senior thesis)
team: ["Thatcher Steele-Maley", "Cooper McCarthy", "Zach Henderson", "Colin Friedel"]
tags: [SOLIDWORKS, Hydrostatic analysis, Marine materials, Pressure vessels, SLS printing, Water testing]
docs:
  - label: "Read the senior thesis (152 pp)"
    url: /assets/docs/iris-thesis.pdf
results:
  - "**Self-righting buoy:** metacentric height GM = +31.5 mm; stayed upright and well above the surface through wind chop in the bay"
  - "**3.33× depth safety factor:** acrylic tube rated to 100 m vs. the 30 m requirement"
  - "**Watertight on first assembly:** passed a 10–15 inHg vacuum test with < 0.5 inHg drop over 10 min"
  - "**Cellular through the dome:** 200+ lines of sensor data sent from the floating buoy with 0.5% loss"
---

## The Problem

The Robotic Systems Lab's REEF sensor network logs data on the Palos Verdes Reef, but getting that data back takes a boat, two divers, and a full day, at roughly $800+ per trip. **IRIS** sits next to REEF on the seafloor. On a schedule, a winch releases a tethered buoy, the buoy surfaces and uploads the data over LTE-M cellular, and the winch reels it back down out of reach of boats and waves.

<figure>
  <img src="/assets/img/projects/iris/conops.jpg" alt="IRIS concept of operations">
  <figcaption>Concept of operations: the buoy stays submerged between cycles, surfaces to transmit, and is retracted.</figcaption>
</figure>

**My piece was the buoy:** it had to keep the electronics dry at depth, let cellular signal through, and float upright with the antenna clear of the water every time it surfaced.

## Buoy Design

### Choosing the Enclosure

- **First option, a donated Blue Ocean Gear buoy shell:** proven for cellular, but it would need a hole bored through it for the data cable, and it was too small to trust while anchored at the surface
- **Final choice, a Blue Robotics watertight enclosure with a polycarbonate dome:** polycarbonate lets cellular signal through (confirmed by Blue Ocean Gear and published antenna-housing data), and the modular end caps take watertight cable penetrators

### Structure

<div class="demo-grid">
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/iris/assembly.jpg"><img class="demo-media" src="/assets/img/projects/iris/assembly.jpg" alt="Final IRIS buoy assembly"></a>
    <div class="demo-text">
    <h3>Final Assembly</h3>
    <ul>
      <li><strong>Pressure vessel:</strong> 300 mm cast acrylic tube; polycarbonate dome on top holds the antenna above the waterline</li>
      <li><strong>Bottom cap:</strong> aluminum, with ten M10 ports for Wet-Link penetrators; dual radial O-rings on both caps</li>
      <li><strong>Depth:</strong> tube 100 m, dome 500 m, cap 1000 m → 3.33× safety factor at 30 m</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/iris/exploded.png"><img class="demo-media" src="/assets/img/projects/iris/exploded.png" alt="Exploded view of the IRIS buoy assembly"></a>
    <div class="demo-text">
    <h3>Exploded View</h3>
    <ul>
      <li><strong>Frame:</strong> anodized aluminum T-slot rails as the structural spine</li>
      <li><strong>Clamps:</strong> 6061-T6 anodized, rubber-lined, with 316 stainless hardware</li>
      <li><strong>Mounts:</strong> SLS nylon (complex geometry, no marine treatment needed), one carrying the tether hardware</li>
      <li><strong>Tether:</strong> two 316 stainless screw-pin shackles rated to 700 lb</li>
    </ul>
    </div>
  </div>
</div>

Every material was chosen to survive a 6-month seawater deployment: anodized aluminum and 316 stainless resist corrosion and galvanic attack, and nothing in water contact is coated.

### Stability Analysis

The buoy has to float upright so the antenna stays above water. I checked this with a hydrostatic model built from a component-by-component inventory of mass and displaced volume.

<figure>
  <img src="/assets/img/projects/iris/stability-diagram.png" alt="Buoy stability diagram showing keel, center of gravity, center of buoyancy, and metacenter">
  <figcaption>When the buoy tilts, the center of buoyancy shifts to B′. Because the metacenter M sits above the center of gravity G, buoyancy creates a righting moment.</figcaption>
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

About **91% of the righting ability comes from the low ballast** (KB − KG = 28.5 mm); the slender tube's waterplane adds only 2.9 mm. The ballast bolts to the T-slot nuts, so its height can be tuned during integration. A sweep checked how far it can move before the buoy becomes unstable:

{% include iris-gm-chart.html %}

## Testing

- **Vacuum leak test:** both enclosures were pulled to 10–15 inHg and had to lose less than 0.5 inHg in 10 minutes; the buoy passed as first assembled
- **Stability and freeboard:** ballast height was tuned in the pool until the buoy reliably righted itself and sat high enough for the antenna

<div class="demo-grid">
  <div class="demo">
    <a class="demo-media-link" href="/assets/img/projects/iris/cellular-tank.jpg"><img class="demo-media" src="/assets/img/projects/iris/cellular-tank.jpg" alt="Buoy floating in the test tank while transmitting"></a>
    <div class="demo-text">
    <h3>Cellular Payload · Test Tank</h3>
    <ul>
      <li>Sent 200+ lines of sample sensor data from the floating buoy, losing one packet (0.5%, under the 1% requirement)</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link" href="/assets/img/projects/iris/buoy-winch-dock.jpg"><img class="demo-media" src="/assets/img/projects/iris/buoy-winch-dock.jpg" alt="IRIS buoy and winch ready for deployment in Foster City"></a>
    <div class="demo-text">
    <h3>Bay Deployment · Foster City</h3>
    <ul>
      <li>5 full winch cycles in open water; the buoy stayed upright and well above the surface through wind chop and wall reflections</li>
      <li>One person could deploy the whole system by lowering it on a rope</li>
    </ul>
    </div>
  </div>
</div>

In the final end-to-end test in SCU's pool, IRIS ran its full cycle with no intervention: the buoy commanded a release, received the data, surfaced, transmitted, and was retracted.

## How the Rest of IRIS Works

*These subsystems were built by my teammates, and are summarized here for context.*

<div class="demo-grid">
  <div class="demo">
    <video class="demo-media" src="/assets/video/iris-brake-servo.mp4" poster="/assets/video/iris-brake-servo.jpg" muted loop playsinline controls preload="metadata" data-autoplay></video>
    <div class="demo-text">
    <h3>Winch & Brake</h3>
    <ul>
      <li><strong>Drive:</strong> Blue Trail SER-2130 submersible servo (CAN, magnetic encoder) through an acetal gearbox</li>
      <li><strong>Brake:</strong> a titanium ratchet and spring pawl hold the positively buoyant buoy down; a second servo lifts the pawl only to release, so it draws no power while holding</li>
      <li><strong>Build:</strong> acetal structure, 316 stainless hardware, polypropylene rope; 100 raise/lower cycles in a repeatability test (a deployment needs 24)</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link" href="/assets/img/projects/iris/reef-node.jpg"><img class="demo-media" src="/assets/img/projects/iris/reef-node.jpg" alt="REEF sensor node deployed underwater"></a>
    <div class="demo-text">
    <h3>Communications & Electronics</h3>
    <ul>
      <li><strong>Subsea:</strong> an Adalogger M0 in a second watertight enclosure pulls data from REEF over RS-485 and drives the winch</li>
      <li><strong>Buoy ↔ seafloor:</strong> Succorfish Delphis acoustic modems</li>
      <li><strong>Buoy → shore:</strong> a Particle Boron 404X sends data over LTE-M cellular to a web dashboard <span class="credit">(photo: REEF sensor node, SCU RSL)</span></li>
    </ul>
    </div>
  </div>
</div>
