---
title: "GOAL! Penalty Shootout Arcade Game"
context: Advanced Mechatronics I (Graduate) · Santa Clara University
summary: A coin-operated, two-player electromechanical arcade game that recreates the pressure of a penalty shootout with real-time motion, sound, and lights.
order: 4
featured: true
thumb: /assets/img/projects/goal/final.jpg
hero_image: /assets/img/projects/goal/final.jpg
role: Mechanical design and fabrication, Arduino game logic, wiring and integration
timeline: Graduate course project
# team: ["Teammate Name"]
tags: [Arduino Mega, SOLIDWORKS, Laser cutting, 3D printing, Servos]
results:
  - "**Ran for 6 hours straight** at a public demo"
  - "**Fully autonomous gameplay:** 10 rounds, sudden death, automatic reset"
  - "**Precise, repeatable motion** through PWM calibration and timing control"
---

## Gameplay

One player controls the kicker and the other the goalkeeper, each with a joystick. A coin starts the match. Players alternate penalties for 10 rounds, with sudden death if tied, while LEDs, a 7-segment scoreboard, and MP3 audio react to each shot.

## Mechanical Design

- **Frame:** laser-cut wood enclosure designed in SOLIDWORKS
- **Kicker:** a hidden **rack-and-pinion run-up** driven by a continuous-rotation servo, with a **magnetic coupling** to the visible player
- **Goalkeeper:** a servo with calibrated dive angles synchronized to the game logic
- **Coin mechanism:** a jam-proof optical coin detector

<div class="gallery">
  <figure><img src="/assets/img/projects/goal/cad.jpg" alt="Enclosure CAD"></figure>
  <figure><img src="/assets/img/projects/goal/goalie.jpg" alt="Goalkeeper mechanism"></figure>
  <figure><img src="/assets/img/projects/goal/coin.jpg" alt="Coin slot"></figure>
</div>

## Electronics and Control

- **Arduino Mega** runs the game state machine: coin → rounds → sudden death → reset
- **Inputs:** two joysticks and the optical coin sensor
- **Outputs:** LED strips, 7-segment displays, MP3 audio, and the kicker and goalkeeper servos
- **Wiring:** power, signal, and actuator lines organized into a clean, serviceable layout

<div class="gallery">
  <figure><img src="/assets/img/projects/goal/electronics.jpg" alt="Electronics breadboard"></figure>
  <figure><img src="/assets/img/projects/goal/wiring.jpg" alt="Final wiring"></figure>
  <figure><img src="/assets/img/projects/goal/build.jpg" alt="Build session"></figure>
</div>

## Results

The finished game ran without interruption through a 6-hour public demo, with full 10-round matches, sudden death, and automatic resets between players.
