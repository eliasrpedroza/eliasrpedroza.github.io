---
title: "GOAL! Penalty Shootout Arcade Game"
context: Advanced Mechatronics I (Graduate) · Santa Clara University
summary: A coin-operated, two-player electromechanical arcade game that recreates the pressure of a penalty shootout with real-time motion, sound, and lights.
order: 4
featured: true
wide: true
thumb: /assets/img/projects/goal/final.jpg
hero_video: /assets/video/goal/gameplay.mp4
hero_poster: /assets/video/goal/gameplay.jpg
hero_max_width: 680px   # keeps the landscape video from taking over the screen
hero_caption: "Full match walkthrough: coin start, countdown, shots and saves, and the end-of-game sequence."
timeline: Fall 2025 (graduate course project)
team: ["Ysidro Magaña"]
tags: [Arduino Mega, SOLIDWORKS, Laser cutting, 3D printing, Servos]
results:
  - "**Ran for 6 hours straight** at a public demo"
  - "**Fully autonomous gameplay:** 10 rounds, sudden death, automatic reset"
  - "**Precise, repeatable motion** through PWM calibration and timing control"
---

## Gameplay

<div class="split" markdown="1">
<div markdown="1">

Two players face off as the shooter and the goalie. A penny starts the game with a countdown and intro audio. Each round, both players get a **10-second countdown** to pick one of five spots with their joystick, and walls between the stations keep each pick hidden.

When the clock hits zero, the picks lock in: **different spot = GOAL!, same spot = SAVE!** The shooter runs up, the goalie dives, and the scoreboard and audio react. Teams switch every shot for 10 rounds, and a draw goes to sudden death.

</div>
<div class="demo-media slideshow" style="aspect-ratio: 6 / 5" data-interval="4000">
  <a class="slide slide--contain is-active" href="/assets/img/projects/goal/instructions-1.jpg" data-label="Instructions pt. 1"><img src="/assets/img/projects/goal/instructions-1.jpg" alt="Laser-engraved instructions, part 1: insert penny, watch the countdown"></a>
  <a class="slide slide--contain" href="/assets/img/projects/goal/instructions-2.jpg" data-label="Instructions pt. 2"><img src="/assets/img/projects/goal/instructions-2.jpg" alt="Laser-engraved instructions, part 2: placement locks at zero, 10 rounds, sudden death"></a>
</div>
</div>

## From Sketch to CAD

<div class="demo-grid">
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/goal/sketch.jpg"><img class="demo-media" src="/assets/img/projects/goal/sketch.jpg" alt="Hand-drawn concept sketch of the penalty shootout game"></a>
    <div class="demo-text">
    <h3>Concept Sketch</h3>
    <ul>
      <li>The first idea: hidden shot/save selectors, a servo goalie with five dive positions, LEDs for goals and misses, and players that run up to the penalty spot</li>
      <li>Buttons became joysticks; the hidden picks, servo goalie, LED scoreboard, and run-up made it to the final build</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/goal/cad.jpg"><img class="demo-media" src="/assets/img/projects/goal/cad.jpg" alt="SOLIDWORKS model of the enclosure, top and isometric views"></a>
    <div class="demo-text">
    <h3>SOLIDWORKS Model</h3>
    <ul>
      <li>Finger-jointed plywood enclosure, laser cut and engraved</li>
      <li>Player stations on each side, walled off so neither player sees the other's pick</li>
    </ul>
    </div>
  </div>
</div>

## Mechanisms

<div class="demo-grid">
  <div class="demo">
    <a class="demo-media-link demo-media-link--fit" href="/assets/img/projects/goal/goalie.jpg"><img class="demo-media" src="/assets/img/projects/goal/goalie.jpg" alt="Laser-cut goalie mounted on a servo behind the goal"></a>
    <div class="demo-text">
    <h3>Goalie</h3>
    <ul>
      <li>Laser-cut keeper mounted on a servo through the backboard</li>
      <li>Calibrated dive angles for all five spots, synced to the game logic</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--fit" href="/assets/img/projects/goal/kicker.jpg"><img class="demo-media" src="/assets/img/projects/goal/kicker.jpg" alt="3D-printed rack and pinion driven by a micro servo, with a magnet on top"></a>
    <div class="demo-text">
    <h3>Shooter Run-Up</h3>
    <ul>
      <li>Hidden 3D-printed rack and pinion under the field, driven by a continuous-rotation servo</li>
      <li>A magnet on the rack drags the visible player along the top, so no mechanism shows on the pitch</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--fit" href="/assets/img/projects/goal/station.jpg"><img class="demo-media" src="/assets/img/projects/goal/station.jpg" alt="Player station with an arcade joystick and engraved direction arrows"></a>
    <div class="demo-text">
    <h3>Player Station</h3>
    <ul>
      <li>Arcade joystick with five marked directions: top left/right, bottom left/right, and middle</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--fit" href="/assets/img/projects/goal/coin.jpg"><img class="demo-media" src="/assets/img/projects/goal/coin.jpg" alt="Coin slot and 3D-printed coin return tray holding a penny"></a>
    <div class="demo-text">
    <h3>Coin Slot</h3>
    <ul>
      <li>Optical sensor detects the penny and boots the game, with no moving parts to jam</li>
      <li>The penny drops into a printed return tray, so players get it back</li>
    </ul>
    </div>
  </div>
</div>

## Electronics

An **Arduino Mega** runs the game as a state machine (coin → countdown → shot → result → next round → sudden death → reset), reading both joysticks and the coin sensor and driving the servos, lights, and audio.

<div class="demo-grid">
  <div class="demo">
    <a class="demo-media-link demo-media-link--fit" href="/assets/img/projects/goal/scoreboard.jpg"><img class="demo-media" src="/assets/img/projects/goal/scoreboard.jpg" alt="Engraved scoreboard with LEDs for each team and a 4-digit display"></a>
    <div class="demo-text">
    <h3>Scoreboard</h3>
    <ul>
      <li>Five LEDs per team (MUN vs. BAR) track goals and misses</li>
      <li>A 4-digit 7-segment display runs the countdown</li>
    </ul>
    </div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--fit" href="/assets/img/projects/goal/audio.jpg"><img class="demo-media" src="/assets/img/projects/goal/audio.jpg" alt="DFPlayer Mini MP3 module on a breadboard"></a>
    <div class="demo-text">
    <h3>Audio</h3>
    <ul>
      <li>DFPlayer Mini plays the intro and game sound effects from a microSD card through two speakers</li>
    </ul>
    </div>
  </div>
</div>

## Looking Back

<div class="split" markdown="1">
<div markdown="1">

The wiring held up through the 6-hour demo, but it was messy. After seeing production wire harnesses on humanoid robots at 1X, I'd rebuild it as a harness: bundled, labeled runs with a connector at each subsystem, so the joysticks, servos, and scoreboard could each be unplugged and serviced on their own.

</div>
<figure>
  <a href="/assets/img/projects/goal/wiring.jpg"><img src="/assets/img/projects/goal/wiring.jpg" alt="Arduino Mega and breadboards with the game's wiring"></a>
  <figcaption>The as-built wiring under the field.</figcaption>
</figure>
</div>
