---
title: Circuits & Embedded Systems Practice
context: Independent practice · Analog, digital & microcontroller
summary: Eight hands-on circuits, from op-amp timers to an ultrasonic rangefinder, built to develop the electronics and embedded skills later used in GOAL! and IRIS.
order: 6
featured: false
thumb: /assets/img/projects/circuits/c-036.jpg
hero_video: /assets/video/circuits/ultrasonic-lcd.mp4
hero_caption: Ultrasonic rangefinder showing live distance readings on an LCD.
tags: [Arduino, Op-amps, 555 timer, Logic gates, PWM, TinkerCAD]
results:
  - "**8 circuits built and verified** across analog, digital, and microcontroller domains"
  - "**Timing circuits on target:** RC delay ≈ 10 s, 555 one-shot ≈ 9–10 s"
  - "**Rangefinder checked against a ruler** at ~20 cm"
  - "**Servo and PWM motor control** carried directly into [GOAL!](/projects/goal-penalty-shootout/)"
---

## Analog & Timing

<div class="demo">
  <video class="demo-media" src="/assets/video/circuits/rc-timer-led.mp4" muted loop playsinline preload="metadata" data-autoplay></video>
  <div class="demo-text">
    <h3>LED Turn-On (RC Timer)</h3>
    <p>A time-delayed LED built entirely from analog components.</p>
    <ul>
      <li><strong>How:</strong> a 10 µF RC network charges toward an op-amp comparator threshold; the comparator switches a transistor that drives the LED</li>
      <li><strong>Timing:</strong> set by τ = RC, so the LED turns on ~10 s after the switch closes</li>
      <li><strong>Key skill:</strong> using an op-amp as a threshold detector and tuning the reference voltage and resistor values</li>
    </ul>
  </div>
</div>

<div class="demo">
  <div class="demo-media demo-pair">
    <img src="/assets/img/projects/circuits/c-031.jpg" alt="Op-amp difference circuit on a breadboard">
    <img src="/assets/img/projects/circuits/c-032.jpg" alt="TinkerCAD simulation of the difference circuit">
  </div>
  <div class="demo-text">
    <h3>Op-Amp Difference Amplifier</h3>
    <p>A subtractor that outputs V<sub>out</sub> = V<sub>1</sub> − V<sub>2</sub> from two potentiometer inputs.</p>
    <ul>
      <li><strong>Supply:</strong> dual ±9 V rails, so the output swings from about +9 V to −9 V</li>
      <li><strong>Validated in TinkerCAD first:</strong> 4.00 V − 6.09 V → −2.09 V; 8.99 V − 1.99 V → 7.00 V</li>
      <li><strong>Main challenge:</strong> building the negative supply rail on the breadboard</li>
    </ul>
  </div>
</div>

<div class="demo">
  <video class="demo-media" src="/assets/video/circuits/555-one-shot.mp4" muted loop playsinline preload="metadata" data-autoplay></video>
  <div class="demo-text">
    <h3>555 One-Shot Timer</h3>
    <p>A button press triggers a 555 in monostable mode, which lights an LED through a transistor for a fixed time.</p>
    <ul>
      <li><strong>Timing:</strong> a 680 µF timing capacitor gives a repeatable ~9–10 s pulse (t ≈ 1.1·RC)</li>
      <li><strong>Verified:</strong> the full trigger → threshold → discharge cycle</li>
    </ul>
  </div>
</div>

## Digital Logic

<div class="demo">
  <video class="demo-media" src="/assets/video/circuits/full-adder.mp4" muted loop playsinline preload="metadata" data-autoplay></video>
  <div class="demo-text">
    <h3>Full Adder</h3>
    <p>Three switches (A, B, C<sub>in</sub>) drive LEDs for SUM and CARRY, built from XOR, AND, and OR gates.</p>
    <ul>
      <li><strong>SUM</strong> = A ⊕ B ⊕ C<sub>in</sub></li>
      <li><strong>CARRY</strong> = A·B + A·C<sub>in</sub> + B·C<sub>in</sub></li>
      <li><strong>Verified:</strong> all 8 input combinations match the truth table</li>
    </ul>
  </div>
</div>

## Microcontroller I/O

<div class="demo">
  <video class="demo-media" src="/assets/video/circuits/digital-io.mp4" muted loop playsinline preload="metadata" data-autoplay></video>
  <div class="demo-text">
    <h3>Digital I/O: Switch-Controlled LEDs</h3>
    <p>Two switches set the behavior of a pair of LEDs.</p>
    <ul>
      <li><strong>STOP/GO:</strong> both LEDs off in STOP</li>
      <li><strong>SLOW/FAST:</strong> ~3 s vs. ~1 s per LED state</li>
      <li><strong>Hardware:</strong> LEDs driven through transistors; switch inputs conditioned so they never float</li>
    </ul>
  </div>
</div>

<div class="demo">
  <video class="demo-media" src="/assets/video/circuits/analog-io.mp4" muted loop playsinline preload="metadata" data-autoplay></video>
  <div class="demo-text">
    <h3>Analog I/O: Potentiometer-Dimmed LED</h3>
    <p>A potentiometer sets LED brightness through the microcontroller.</p>
    <ul>
      <li><strong>Signal path:</strong> potentiometer → ADC reading → mapped to a PWM duty cycle → transistor-driven LED</li>
      <li><strong>Result:</strong> perceived brightness tracks the duty cycle smoothly across the pot's range</li>
    </ul>
  </div>
</div>

<div class="demo">
  <img class="demo-media" src="/assets/img/projects/circuits/c-033.jpg" alt="Ultrasonic sensor and LCD on a breadboard">
  <div class="demo-text">
    <h3>Ultrasonic Rangefinder with LCD</h3>
    <p>An HC-SR04 sensor measures distance and displays it live on a 16-pin character LCD (video at top of page).</p>
    <ul>
      <li><strong>Distance:</strong> computed from echo time and the speed of sound, halved for the round trip</li>
      <li><strong>Display:</strong> a potentiometer sets LCD contrast</li>
      <li><strong>Verified:</strong> an object ~20 cm away, checked with a ruler</li>
    </ul>
  </div>
</div>

## Actuators

<div class="demo">
  <img class="demo-media" src="/assets/img/projects/circuits/c-035.jpg" alt="Microcontroller driving a motor and servo">
  <div class="demo-text">
    <h3>DC Motor & Servo Control</h3>
    <ul>
      <li><strong>DC motor:</strong> a switch sets direction and a potentiometer sets PWM speed, with motor power kept separate from control logic</li>
      <li><strong>Positional servo:</strong> steps through left, center, and right positions</li>
      <li><strong>Continuous-rotation servo:</strong> speed and direction set by the control signal</li>
      <li><strong>Applied in <a href="/projects/goal-penalty-shootout/">GOAL!</a>:</strong> the goalkeeper servo and the continuous-servo rack-and-pinion run-up</li>
    </ul>
  </div>
</div>

## Takeaways

These builds covered the fundamentals behind every later electromechanical project: RC and 555 timing, op-amp signal conditioning, transistor drivers, clean digital inputs, ADC-to-PWM control, sensor timing, and motor and servo control.
