---
title: ROS 2 Waypoint Follower
context: Course project · Embedded Systems in Robotics, Northwestern
summary: A ROS 2 system that drives a simulated robot through a loop of waypoints with a feedback controller, while a second node injects noise into its motor commands. Built from scratch in Python with custom services and messages.
order: 1
thumb: /assets/img/projects/turtle/thumb.jpg
preview: /assets/video/previews/turtle.mp4   # plays on the home-page card while hovered
hero_video: /assets/video/turtle/waypoints.mp4
hero_poster: /assets/video/turtle/waypoints.jpg
hero_portrait: true
hero_side: true
hero_caption: "Load, start, pause, and resume through the /toggle service, then one full lap through six waypoints (2× speed while moving). Pink markers point to the next waypoint; orange is the path driven."
timeline: Oct 2026
tags: [ROS 2, Python, Feedback control, Linux]
results:
  - "**Closed-loop control at 100 Hz** reaches every waypoint despite noise on every velocity command"
  - "**One lap in 19.13 s:** drove 32.86 m vs. the 33.19 m straight-line loop, cutting corners within the 0.04 m arrival tolerance"
  - "**Custom ROS 2 interfaces:** a service to load waypoints and a message reporting distance, error, and time each lap"
---

## System

<figure>
  <a href="/assets/img/projects/turtle/rqt-graph.png"><img src="/assets/img/projects/turtle/rqt-graph.png" alt="rqt_graph of the running system: waypoint, corrupt, and turtlesim nodes and the topics between them"></a>
  <figcaption>The running system in rqt_graph. The waypoint node also calls turtlesim's <code>reset</code>, <code>set_pen</code>, and <code>teleport_absolute</code> services to draw the markers.</figcaption>
</figure>

- **waypoint:** loads waypoints through a custom `LoadWaypoints` service, starts and stops on `/toggle`, and steers toward the current target using pose feedback
- **corrupt:** sits between the controller and the robot and adds Gaussian noise proportional to each command, like motors that don't quite do what they're told
- **Launch file:** starts all three nodes and sets each node's parameters (control rate, arrival tolerance, noise level, background color)

## Running It

**Start / stop:** each `/toggle` call flips the robot between moving and stopped, and the lap timer pauses while it's stopped.

<figure><img src="/assets/img/projects/turtle/terminal-toggle.png" alt="Terminal showing a /toggle service call and its response"></figure>

**Lap metrics:** after each lap the node publishes its custom `ErrorMetric` message: here 32.86 m driven, −0.33 m vs. the ideal loop, in 19.13 s of moving time.

<figure><img src="/assets/img/projects/turtle/terminal-metrics.png" alt="ros2 topic echo /loop_metrics showing complete_loops 1, actual_distance 32.86, error -0.33, time 19.13"></figure>

## Controller

- **Heading:** the error to the target is wrapped to ±π so the robot always turns the short way, and the turn rate is 6× that error
- **Speed:** it only drives forward once it's pointed within 0.2 rad of the target, at 1.5× the remaining distance, so it slows as it arrives
- **Arrival:** within 0.04 m, it moves on to the next waypoint; finishing the loop publishes the lap's distance, error, and time

## Drawing the Markers

When waypoints load, the node resets the sim and draws a triangle at each one, pointing toward the next. It chains turtlesim's `set_pen` and `teleport_absolute` services with **async service calls in their own callback group**, so the node can wait on turtlesim from inside a service callback without deadlocking. I worked out the geometry by hand first: forward along the heading (cos θ, sin θ) for the tip, and sideways (−sin θ, cos θ) for the base corners.

<div class="demo-grid">
  <div class="demo">
    <video class="demo-media" style="aspect-ratio: 1 / 1" src="/assets/video/turtle/drawing.mp4" poster="/assets/video/turtle/drawing.jpg" muted loop playsinline controls preload="metadata" data-autoplay></video>
    <div class="demo-text"><h3>Markers being drawn</h3><p>Slowed down 2.5×: the turtle teleports with the pen up and down to trace each triangle.</p></div>
  </div>
  <div class="demo">
    <a class="demo-media-link demo-media-link--fit" style="aspect-ratio: 1 / 1" href="/assets/img/projects/turtle/triangle-sketch.jpg"><img class="demo-media" src="/assets/img/projects/turtle/triangle-sketch.jpg" alt="Hand sketch of the triangle-drawing geometry and pen-up/pen-down sequence"></a>
    <div class="demo-text"><h3>Planning sketch</h3><p>The pen-up/pen-down sequence and the geometry for each triangle.</p></div>
  </div>
</div>
