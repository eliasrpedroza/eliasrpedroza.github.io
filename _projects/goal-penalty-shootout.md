---
title: "GOAL! Penalty Shootout Arcade Game"
context: Advanced Mechatronics I (Graduate) · Santa Clara University
summary: A coin-operated, two-player electromechanical arcade game that recreates the pressure of a penalty shootout with real-time motion, sound, and lights.
order: 4
featured: true
thumb: /assets/img/projects/goal/final.jpg
hero_video: /assets/video/goal/gameplay.mp4
hero_poster: /assets/video/goal/gameplay.jpg
hero_caption: "Full match walkthrough: coin start, countdown, shots and saves, and the end-of-game sequence."
timeline: Fall 2025 (graduate course project)
team: ["Ysidro Magaña"]
team_note: "We designed, built, and programmed every part of the game together."
tags: [Arduino Mega, SOLIDWORKS, Laser cutting, 3D printing, Servos]
results:
  - "**Ran for 6 hours straight** at a public demo"
  - "**Fully autonomous gameplay:** 10 rounds, sudden death, automatic reset"
  - "**Precise, repeatable motion** through PWM calibration and timing control"
---

## Gameplay

Two players face off as the kicker and the goalkeeper. A penny starts the game with a countdown and intro audio. Each round, both players get a **10-second countdown** to pick a direction on their joystick, with walls between the stations so neither can see the other's pick. The kicker runs up, the goalkeeper dives, and the LED scoreboard, 7-segment display, and audio react to the result. Players alternate for 10 shots, and a draw goes to sudden death.

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
- **Wiring:** separate power, signal, and actuator runs that held up through a 6-hour public demo

<div class="gallery">
  <figure><img src="/assets/img/projects/goal/electronics.jpg" alt="Electronics breadboard"></figure>
  <figure><img src="/assets/img/projects/goal/wiring.jpg" alt="Final wiring"></figure>
  <figure><img src="/assets/img/projects/goal/build.jpg" alt="Build session"></figure>
</div>

## Looking Back

The wiring worked, but it was point-to-point. After seeing production wire harnesses on humanoid robots at 1X, I'd rebuild it as a harness: bundled, labeled runs with a connector at each subsystem, so the joysticks, servos, and scoreboard could each be unplugged and serviced on their own.
