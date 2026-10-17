---
title: Jamming-Based Prosthetic Hand
context: Research · DART Lab, Santa Clara University
summary: I designed the variable-stiffness fingers for a low-cost, body-powered prosthetic hand. Laminar-jamming joints are flexible for closing around an object, then lock rigid under vacuum to hold the grasp. Accepted to IEEE-RAS Humanoids 2026.
order: 3
wide: true
thumb: /assets/img/projects/dart/thumb.jpg
hero_side: true
hero_slides_ratio: 1 / 1
hero_slides_interval: 3500
hero_slides:
  - src: /assets/img/projects/dart/finger-keys.jpg
    label: Holding keys
    alt: Both fingers locked around a set of keys, with the red return bands visible on the back of each finger
  - src: /assets/img/projects/dart/finger-weight.jpg
    label: Holding weight under vacuum
    alt: Red finger locked in a bent pose under vacuum, holding a hanging weight
  - src: /assets/img/projects/dart/finger-grasp.jpg
    label: Two-finger grasp
    alt: Two fingers locked around a box of gloves
hero_caption: Under vacuum the finger joints lock and hold the grasp; the red bands on the back pull the fingers open again when released.
role: "Finger subsystem: laminar-jamming flexures, molds, finger structure and tube routing, whiffletree, and early test rigs"
timeline: Jun 2025 – Jun 2026
team: ["Sophie Jacqmotte-Parks", "Nicos Katigbak", "Parnia Ayoubi"]
team_note: "Advised by Prof. Michael Abbott. Teammates led the palm and the published testing."
tags: [Soft robotics, Silicone molding, Prototyping, MATLAB, SOLIDWORKS, Mechanical testing]
results:
  - "**Working jamming finger:** holds a load rigidly under vacuum and springs back when released"
  - "**55% thinner flexures** after iterating geometry and paper grit"
  - "**Finger stiffness 2.3× higher** under vacuum in the published tests (0.05 → 0.11 N/mm)"
  - "**Co-author, IEEE-RAS Humanoids 2026**"
---

<div class="callout" markdown="1">
**Publication** · S. Jacqmotte-Parks, N. M. Katigbak, **E. Pedroza**, P. Ayoubi, and M. E. Abbott, "Design and Characterization of a Jamming-Based Low-Cost Prosthetic Hand," accepted to the *2026 IEEE-RAS 25th International Conference on Humanoid Robots (Humanoids 2026)*, Santa Clara, CA.
</div>

## How It Works

Body-powered prostheses are cheap, but the user has to keep pulling on a shoulder harness to hold a grasp, which is tiring. **Laminar jamming** fixes that in the fingers: a stack of sandpaper sheets sealed in a silicone chamber slides freely at normal pressure, then clamps together under vacuum. The user closes the fingers with the harness, and vacuum locks them in that pose.

## My Work

<div class="demo-grid">
  <div class="demo">
    <div class="demo-media slideshow">
      <a class="slide slide--contain is-active" href="/assets/img/projects/dart/finger.jpg" data-label="Final finger"><img src="/assets/img/projects/dart/finger.jpg" alt="Side view of the final finger showing the DIP and PIP jamming joints"></a>
      <a class="slide slide--contain" href="/assets/img/projects/dart/proto-pair.jpg" data-label="Double-flexure prototype"><img src="/assets/img/projects/dart/proto-pair.jpg" alt="Two earlier double-flexure fingers with shared vacuum tubing"></a>
      <a class="slide slide--contain" href="/assets/img/projects/dart/proto-early.jpg" data-label="Early prototype"><img src="/assets/img/projects/dart/proto-early.jpg" alt="Early 3D-printed finger prototype with a silicone flexure"></a>
    </div>
    <div class="demo-text">
    <h3>Finger</h3>
    <ul>
      <li><strong>Final flexure:</strong> 25 sheets of P600 sandpaper in a 6 mm chamber of Mold Star 40T silicone, with ~1 mm walls, running the full finger to form the PIP and DIP joints</li>
      <li><strong>Structure:</strong> I designed the 3D-printed segments, cable path, and vacuum tube routing, curved out the back to clear the base joint's spring</li>
      <li><strong>Motion:</strong> cables close the finger, vacuum locks it, and rubber bands on the back reopen it</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/dart/dorsal-view.jpg"><img class="demo-media" src="/assets/img/projects/dart/dorsal-view.jpg" alt="Back of the hand with the whiffletree and cable routing highlighted"></a>
    <div class="demo-text">
    <h3>Whiffletree</h3>
    <ul>
      <li>Splits one cable pull from the harness across both fingers, so they close together and wrap around uneven objects</li>
      <li>Scaled down to fit the back of the hand; I started a more compact drum-based version for the next design</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <div class="demo-media slideshow">
      <a class="slide slide--contain is-active" href="/assets/img/projects/dart/mold-exploded.jpg" data-label="Mold CAD"><img src="/assets/img/projects/dart/mold-exploded.jpg" alt="Exploded CAD of the 3-part flexure mold with the core and tube path"></a>
      <a class="slide" href="/assets/img/projects/dart/mold-photo.jpg" data-label="Printed mold"><img src="/assets/img/projects/dart/mold-photo.jpg" alt="3D-printed mold with a cured silicone flexure inside"></a>
      <a class="slide slide--contain" href="/assets/img/projects/dart/flexure-cast.jpg" data-label="Cast flexure"><img src="/assets/img/projects/dart/flexure-cast.jpg" alt="Cast double flexure with an angled tube exit"></a>
    </div>
    <div class="demo-text">
    <h3>Molds &amp; Casting</h3>
    <ul>
      <li>3-part printed molds (top, core, base); the core forms the sealed chamber and the tube path</li>
      <li>A double-flexure mold with an angled tube exit fixed early leaks and tubes slipping out</li>
      <li>Sandpaper goes in through a slit, then sealed with Sil-Poxy</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/dart/deflection-plot.png"><img class="demo-media" src="/assets/img/projects/dart/deflection-plot.png" alt="Deflection vs. load for flexures with different layer materials at -700 mmHg"></a>
    <div class="demo-text">
    <h3>Layers &amp; Geometry</h3>
    <ul>
      <li><strong>Layers:</strong> compared copy paper and P180–P800 sandpaper; mid grits jammed best, P180 was too thick and copy paper too slick</li>
      <li><strong>Geometry:</strong> stiffness scales with thickness cubed, so I added thickness before width; a plain rectangular stack beat an I-beam layout</li>
      <li><strong>Result:</strong> flexures 55% thinner, walls cut from ~1.5 to ~1 mm</li>
    </ul>
    </div>
  </div>
</div>

## Testing

<div class="split" markdown="1">
<div markdown="1">

- **Proof of concept:** bent the finger, pulled vacuum, and hung weights from the tip; it held its pose, then relaxed when the vacuum was released
- **Early rigs (mine):** settled on a one-sided clamp with a point load at the tip, after a two-ended rig twisted the flexure
- **Published test (team):** a force gauge on a linear stage pushed the fingertip 40 mm at 0–700 mmHg. Stiffness rose with vacuum to 4.9 N at the tip; thicker flexures are the next step toward the 10–15 N grasp benchmark

</div>
<div class="demo-media slideshow" style="aspect-ratio: 4 / 3">
  <a class="slide slide--contain is-active" href="/assets/img/projects/dart/finger-stiffness.jpg" data-label="Stiffness vs. vacuum"><img src="/assets/img/projects/dart/finger-stiffness.jpg" alt="Force vs. tip deflection for the finger from 0 to 700 mmHg"></a>
  <a class="slide slide--contain" href="/assets/img/projects/dart/finger-test.jpg" data-label="Test setup"><img src="/assets/img/projects/dart/finger-test.jpg" alt="Finger mounted under a Mark-10 force gauge for stiffness testing"></a>
</div>
</div>

## The Full Hand

<div class="split" markdown="1">
<div markdown="1">

*Built and tested as a team; shown for context.*

The hand pairs my fingers with a granular-jamming palm (a balloon of glass beads) and weighs 529 g, with under $70 in parts. Worn on a body-powered simulator, it handled wrap, pinch, and palmar grasps, and in pullout tests the jamming palm held up to **52.9 N**, matching or beating a rigid palm in every case.

</div>
<div class="demo-media slideshow" style="aspect-ratio: 4 / 3">
  <a class="slide slide--contain is-active" href="/assets/img/projects/dart/hand-on-sim.jpg" data-label="On the body simulator"><img src="/assets/img/projects/dart/hand-on-sim.jpg" alt="The hand worn on a body-powered prosthesis simulator"></a>
  <a class="slide slide--contain" href="/assets/img/projects/dart/grasps.jpg" data-label="Everyday grasps"><img src="/assets/img/projects/dart/grasps.jpg" alt="The hand grasping a door handle, a bottle, keys, and a hex key"></a>
  <a class="slide slide--contain" href="/assets/img/projects/dart/pullout.jpg" data-label="Pullout force"><img src="/assets/img/projects/dart/pullout.jpg" alt="Grasp pullout force at 0, 45, and 90 degrees for four objects and four palm conditions"></a>
</div>
</div>
