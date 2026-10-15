---
title: Circuits & Embedded Systems Practice
context: Independent practice · Sensors, actuators & circuits
summary: Eight hands-on builds, from an ultrasonic rangefinder and PWM motor control to op-amp and 555 timing circuits, that built the embedded and electronics skills later used in GOAL! and IRIS.
order: 6
featured: false
thumb: /assets/img/projects/circuits/thumb.jpg
tags: [Arduino, C++, Sensor integration, PWM motor control, Servo control, Analog circuits]
results:
  - "**Ultrasonic rangefinder** with live LCD readout, verified against a ruler at ~20 cm"
  - "**PWM motor and servo control** carried directly into [GOAL!](/projects/goal-penalty-shootout/)"
  - "**Analog timing on target:** RC delay ≈ 10 s, 555 one-shot ≈ 9–10 s"
  - "**8 circuits built and verified** across sensing, actuation, analog, and digital logic"
wide: true   # wider page column so the two-across grid has room
---

## Sensing & Actuation

<div class="demo-grid">
  <div class="demo">
    <video class="demo-media" src="/assets/video/circuits/ultrasonic-lcd.mp4" poster="/assets/video/circuits/ultrasonic-lcd.jpg" muted loop playsinline controls preload="metadata" data-autoplay></video>
    <div class="demo-text">
    <h3>Ultrasonic Rangefinder with LCD</h3>
    <p>HC-SR04 distance shown live on a 16-pin character LCD.</p>
    <ul>
      <li><strong>Distance:</strong> echo time × speed of sound, halved for the round trip</li>
      <li><strong>Display:</strong> potentiometer sets LCD contrast</li>
      <li><strong>Verified:</strong> object at ~20 cm, checked with a ruler</li>
    </ul>
    </div>
  </div>

  <div class="demo">
    <video class="demo-media" src="/assets/video/circuits/analog-io.mp4" poster="/assets/video/circuits/analog-io.jpg" muted loop playsinline controls preload="metadata" data-autoplay></video>
    <div class="demo-text">
    <h3>Analog I/O: Potentiometer-Dimmed LED</h3>
    <p>A potentiometer sets LED brightness through the microcontroller.</p>
    <ul>
      <li><strong>Signal path:</strong> pot → ADC → PWM duty cycle → transistor-driven LED</li>
      <li><strong>Result:</strong> brightness tracks the duty cycle smoothly</li>
    </ul>
    </div>
  </div>

  <div class="demo">
    <video class="demo-media" src="/assets/video/circuits/digital-io.mp4" poster="/assets/video/circuits/digital-io.jpg" muted loop playsinline controls preload="metadata" data-autoplay></video>
    <div class="demo-text">
    <h3>Digital I/O: Switch-Controlled LEDs</h3>
    <p>Two switches set the behavior of a pair of LEDs.</p>
    <ul>
      <li><strong>STOP/GO:</strong> both LEDs off in STOP</li>
      <li><strong>SLOW/FAST:</strong> ~3 s vs. ~1 s per LED state</li>
      <li><strong>Hardware:</strong> transistor-driven LEDs; switch inputs conditioned so they never float</li>
    </ul>
    </div>
  </div>

  <div class="demo">
    <a class="demo-media-link" href="/assets/img/projects/circuits/c-035.jpg"><img class="demo-media" src="/assets/img/projects/circuits/c-035.jpg" alt="DC Motor & Servo Control"></a>
    <div class="demo-text">
    <h3>DC Motor & Servo Control</h3>
    <ul>
      <li><strong>DC motor:</strong> switch sets direction, pot sets PWM speed; motor power isolated from logic</li>
      <li><strong>Servos:</strong> positional (left/center/right) and continuous-rotation speed/direction control</li>
      <li><strong>Applied in <a href="/projects/goal-penalty-shootout/">GOAL!</a>:</strong> goalkeeper servo and rack-and-pinion run-up</li>
    </ul>
    </div>
  </div>
</div>

## Analog & Digital Circuits

<div class="demo-grid">
  <div class="demo">
    <a class="demo-media-link demo-media-link--diagram" href="/assets/img/projects/circuits/opamp-tinkercad.png"><img class="demo-media" src="/assets/img/projects/circuits/opamp-tinkercad.png" alt="TinkerCAD simulation of the op-amp difference amplifier: V1 = 8.99 V, V2 = 1.99 V, output 7.00 V"></a>
    <div class="demo-text">
    <h3>Op-Amp Difference Amplifier</h3>
    <p>V<sub>out</sub> = V<sub>1</sub> − V<sub>2</sub> from two potentiometer inputs.</p>
    <ul>
      <li><strong>Supply:</strong> dual ±9 V rails; output swings ~+9 V to −9 V</li>
      <li><strong>Simulated in TinkerCAD:</strong> 8.99 V − 1.99 V → 7.00 V (shown); 4.00 V − 6.09 V → −2.09 V</li>
      <li><strong>Main challenge:</strong> building the negative supply rail</li>
      <li><a href="/assets/img/projects/circuits/c-031.jpg">See the breadboard build →</a></li>
    </ul>
    </div>
  </div>

  <div class="demo">
    <video class="demo-media" src="/assets/video/circuits/rc-timer-led.mp4" poster="/assets/video/circuits/rc-timer-led.jpg" muted loop playsinline controls preload="metadata" data-autoplay></video>
    <div class="demo-text">
    <h3>LED Turn-On (RC Timer)</h3>
    <p>A time-delayed LED built entirely from analog parts.</p>
    <ul>
      <li><strong>How:</strong> 10 µF RC network charges to an op-amp comparator threshold, which switches a transistor</li>
      <li><strong>Timing:</strong> τ = RC gives a ~10 s delay</li>
      <li><strong>Key skill:</strong> op-amp as a threshold detector</li>
    </ul>
    </div>
  </div>

  <div class="demo">
    <video class="demo-media" src="/assets/video/circuits/555-one-shot.mp4" poster="/assets/video/circuits/555-one-shot.jpg" muted loop playsinline controls preload="metadata" data-autoplay></video>
    <div class="demo-text">
    <h3>555 One-Shot Timer</h3>
    <p>A button press triggers a 555 in monostable mode to light an LED.</p>
    <ul>
      <li><strong>Timing:</strong> 680 µF capacitor gives a repeatable ~9–10 s pulse (t ≈ 1.1·RC)</li>
      <li><strong>Verified:</strong> full trigger → threshold → discharge cycle</li>
    </ul>
    </div>
  </div>

  <div class="demo">
    <video class="demo-media" src="/assets/video/circuits/full-adder.mp4" poster="/assets/video/circuits/full-adder.jpg" muted loop playsinline controls preload="metadata" data-autoplay></video>
    <div class="demo-text">
    <h3>Full Adder</h3>
    <p>Switches A, B, C<sub>in</sub> drive SUM and CARRY LEDs through XOR, AND, and OR gates.</p>
    <ul>
      <li><strong>SUM</strong> = A ⊕ B ⊕ C<sub>in</sub></li>
      <li><strong>CARRY</strong> = A·B + A·C<sub>in</sub> + B·C<sub>in</sub></li>
      <li><strong>Verified:</strong> all 8 input combinations match the truth table</li>
    </ul>
    </div>
  </div>
</div>

## Takeaways

These builds covered the fundamentals behind every later electromechanical project: sensor timing, ADC-to-PWM control, clean digital inputs, motor and servo drive, transistor switching, op-amp signal conditioning, and RC and 555 timing.
