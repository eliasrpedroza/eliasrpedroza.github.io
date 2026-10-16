---
title: Jamming-Based Prosthetic Hand
context: Research · DART Lab, Santa Clara University
summary: I designed the variable-stiffness fingers for a low-cost, body-powered prosthetic hand. Laminar-jamming joints are flexible for closing around an object, then lock rigid under vacuum to hold the grasp. Accepted to IEEE-RAS Humanoids 2026.
order: 2
wide: true
thumb: /assets/img/projects/dart/thumb.jpg
hero_side: true
hero_slides_ratio: 3 / 4
hero_slides_interval: 3200
hero_slides:
  - src: /assets/img/projects/dart/finger-weight.jpg
    label: Holding weight under vacuum
    alt: Red finger locked in a bent pose under vacuum, holding a hanging weight
  - src: /assets/img/projects/dart/finger-grasp.jpg
    label: Two-finger grasp
    alt: Two fingers locked around a box of gloves
  - src: /assets/img/projects/dart/two-finger.jpg
    label: Fingers on the palm
    alt: Two jamming fingers mounted above the jamming palm
hero_caption: Under vacuum, the finger joints lock in place and hold a load; release the vacuum and they go soft again.
role: "Finger subsystem: laminar-jamming flexures, molds, finger structure and tube routing, whiffletree, and early test rigs"
timeline: Jun 2025 – Jun 2026
team: ["Sophie Jacqmotte-Parks", "Nicos Katigbak", "Parnia Ayoubi"]
team_note: "Advised by Prof. Michael Abbott. Teammates led the palm and the published testing."
tags: [SOLIDWORKS, Silicone molding, 3D printing, Soft robotics, Mechanical testing, MATLAB]
results:
  - "**Working jamming finger:** holds a load rigidly under vacuum and springs back when released"
  - "**55% thinner flexures** after iterating geometry and paper grit"
  - "**Finger stiffness 2.3× higher** under vacuum in the published tests (0.05 → 0.11 N/mm)"
  - "**Co-author, IEEE-RAS Humanoids 2026** (38% acceptance rate)"
---

<div class="callout" markdown="1">
**Publication** · S. Jacqmotte-Parks, N. M. Katigbak, **E. Pedroza**, P. Ayoubi, and M. E. Abbott, "Design and Characterization of a Jamming-Based Low-Cost Prosthetic Hand," accepted to the *2026 IEEE-RAS 25th International Conference on Humanoid Robots (Humanoids 2026)*, Santa Clara, CA.
</div>

## How It Works

Body-powered prostheses are cheap, but the user has to keep pulling on a shoulder harness to hold a grasp, which is tiring. **Laminar jamming** fixes that in the fingers: a stack of sandpaper sheets sealed in a silicone chamber slides freely at normal pressure, then clamps together under vacuum. The user closes the fingers with the harness, and vacuum locks them in that pose.

## Flexures

<div class="demo-grid">
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
      <li>Double-flexure mold with an angled tube exit fixed early leaks and tubes slipping out</li>
      <li>Cast in Mold Star 40T silicone, then sandpaper slid in through a slit sealed with Sil-Poxy</li>
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
      <li><strong>Result:</strong> flexures cut 55% thinner while keeping stiffness control</li>
    </ul>
    </div>
  </div>
</div>

## Finger Design

<div class="demo-grid">
  <div class="demo">
    <div class="demo-media slideshow">
      <a class="slide slide--contain is-active" href="/assets/img/projects/dart/proto-early.jpg" data-label="Early prototype"><img src="/assets/img/projects/dart/proto-early.jpg" alt="Early 3D-printed finger prototype with a silicone flexure"></a>
      <a class="slide slide--contain" href="/assets/img/projects/dart/proto-pair.jpg" data-label="Double flexure"><img src="/assets/img/projects/dart/proto-pair.jpg" alt="Two double-flexure fingers with shared vacuum tubing"></a>
      <a class="slide slide--contain" href="/assets/img/projects/dart/finger.jpg" data-label="Published finger"><img src="/assets/img/projects/dart/finger.jpg" alt="Side view of the final finger showing the DIP and PIP jamming joints"></a>
    </div>
    <div class="demo-text">
    <h3>Finger Iterations</h3>
    <ul>
      <li>One flexure spans both the PIP and DIP joints, with 3D-printed segments around it for structure and cable routing</li>
      <li>I designed the segments, cable path, and vacuum tube routing, curved out the back to clear the base joint's spring</li>
      <li>Cables close the finger, vacuum locks it, and rubber bands on the back reopen it</li>
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
</div>

## Testing

<div class="demo-grid">
  <div class="demo">
    <a class="demo-media-link demo-media-link--fit" href="/assets/img/projects/dart/proto-red.jpg"><img class="demo-media" src="/assets/img/projects/dart/proto-red.jpg" alt="Finger locked under vacuum holding a hanging weight"></a>
    <div class="demo-text">
    <h3>Proof of Concept</h3>
    <ul>
      <li>Bent the finger, pulled vacuum, and hung weights from the tip: it held its pose, then relaxed when the vacuum was released</li>
      <li>Built the early rigs, settling on a one-sided clamp with a point load at the tip to avoid twisting the flexure</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <div class="demo-media slideshow">
      <a class="slide slide--contain is-active" href="/assets/img/projects/dart/finger-test.jpg" data-label="Test setup"><img src="/assets/img/projects/dart/finger-test.jpg" alt="Finger mounted under a Mark-10 force gauge for stiffness testing"></a>
      <a class="slide slide--contain" href="/assets/img/projects/dart/finger-stiffness.jpg" data-label="Results"><img src="/assets/img/projects/dart/finger-stiffness.jpg" alt="Force vs. tip deflection for the finger from 0 to 700 mmHg"></a>
    </div>
    <div class="demo-text">
    <h3>Published Stiffness Test</h3>
    <ul>
      <li>Force gauge on a linear stage pushes the fingertip 40 mm at 0–700 mmHg <span class="credit">(team test)</span></li>
      <li>Stiffness rises with vacuum, up to 4.9 N at the tip; thicker flexures are the next step toward the 10–15 N grasp benchmark</li>
    </ul>
    </div>
  </div>
</div>

## The Full Hand

*Built and tested as a team; shown for context. The hand pairs my fingers with a granular-jamming palm (a balloon of glass beads) and weighs 529 g, with under $70 in parts.*

<div class="demo-grid">
  <div class="demo">
    <div class="demo-media slideshow">
      <a class="slide slide--contain is-active" href="/assets/img/projects/dart/hand-on-sim.jpg" data-label="On the body simulator"><img src="/assets/img/projects/dart/hand-on-sim.jpg" alt="The hand worn on a body-powered prosthesis simulator"></a>
      <a class="slide slide--contain" href="/assets/img/projects/dart/palm-view.jpg" data-label="Palm side"><img src="/assets/img/projects/dart/palm-view.jpg" alt="Palm view with the jamming palm, fingers, and thumb"></a>
      <a class="slide slide--contain" href="/assets/img/projects/dart/grasps.jpg" data-label="Everyday grasps"><img src="/assets/img/projects/dart/grasps.jpg" alt="The hand grasping a door handle, a bottle, keys, and a hex key"></a>
    </div>
    <div class="demo-text">
    <h3>Prototype &amp; Grasps</h3>
    <ul>
      <li>Worn on a body-powered simulator: wrap grasps (door handle, bottle), a pinch (keys), and a palmar grasp on a flat hex key</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/dart/pullout.jpg"><img class="demo-media" src="/assets/img/projects/dart/pullout.jpg" alt="Grasp pullout force at 0, 45, and 90 degrees for four objects and four palm conditions"></a>
    <div class="demo-text">
    <h3>Pullout Force</h3>
    <ul>
      <li>Grip rose with vacuum, up to <strong>52.9 N</strong>, matching or beating a rigid palm in every object and pull-angle case</li>
    </ul>
    </div>
  </div>
</div>
