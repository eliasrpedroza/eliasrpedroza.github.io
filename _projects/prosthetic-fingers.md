---
title: Variable-Stiffness Prosthetic Fingers
context: Research · DART Lab, Santa Clara University
summary: Laminar-jamming fingers for a low-cost prosthetic hand that switches between soft, conforming grasps and stiff, load-bearing ones.
order: 2
featured: true
thumb: /assets/img/projects/dart/fingers.jpg
hero_image: /assets/img/projects/dart/collage.jpg
role: Owned the finger subsystem, including flexures, molds, test rigs, and finger integration
timeline: Jun 2025 – Jun 2026
team: ["Sophie Jacqmotte-Parks", "Nicolas Katigbak"]
team_note: "Teammates led other subsystems of the hand; this page covers the finger subsystem."
tags: [SOLIDWORKS, Silicone molding, 3D printing, MATLAB, Test rigs]
results:
  - "**55% thinner flexures** with better stiffness control and ergonomics"
  - "**Repeatable stiffness characterization** from purpose-built test rigs"
  - "**Reliable grasping under vacuum**, with a whiffletree sharing load across the fingers"
---

## Concept

Jamming changes stiffness on demand. Layers of material (laminar jamming) or loose grains (granular jamming) sit inside a sealed skin. At atmospheric pressure the structure is flexible. When vacuum is applied, friction locks the layers or grains together and it stiffens. The hand uses **laminar-jamming flexures as finger joints** and a **granular-jamming palm**.

## Laminar-Jamming Flexures

Flexure performance was iterated across four variables:

- **Geometry and wall thickness:** thinner walls give a more natural finger profile
- **Layer material:** copy paper and several sandpaper grits (P180–P800) to vary interlayer friction
- **Internal media:** how the layers are packed and sealed
- **Molds:** custom 3D-printed silicone molds sized for the finger assemblies

<div class="gallery">
  <figure><img src="/assets/img/projects/dart/molds.jpg" alt="Silicone molds and flexures"></figure>
  <figure><img src="/assets/img/projects/dart/cad.jpg" alt="Flexure and mold CAD"></figure>
</div>

## Characterization

Test rigs measured **pressure vs. deflection** and **weight vs. deflection** under controlled loading, so flexure variants could be compared directly.

<figure>
  <img src="/assets/img/projects/dart/deflection-plot.png" alt="Deflection vs weight for laminar joints at -700 mmHg">
  <figcaption>Deflection vs. load at −700 mmHg for four layer materials. Rougher layers stay stiffer.</figcaption>
</figure>

## Finger and Palm Integration

- **Actuation:** cable-driven flexion with return springs, plus vacuum routing to each joint
- **Load sharing:** a **whiffletree** mechanism distributes one actuation input across several fingers, so they conform to irregular objects
- **Mounting:** a threaded interface attaches the hand to the socket

<div class="gallery">
  <figure><img src="/assets/img/projects/dart/fingers.jpg" alt="Finger assemblies"></figure>
  <figure><img src="/assets/img/projects/dart/interface.jpg" alt="Threaded mounting interface"></figure>
</div>

## Results

The redesigned flexures are 55% thinner and still give finer stiffness control. The test rigs produced repeatable stiffness data, and the integrated fingers grasped reliably under vacuum, moving the project toward full-hand testing.
