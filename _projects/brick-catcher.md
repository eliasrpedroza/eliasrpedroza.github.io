---
title: Brick-Catching Robot
context: Course project · Embedded Systems in Robotics, Northwestern
summary: A simulated robot in ROS 2 that decides if it can reach a falling brick in time, catches it, and tips it off. The physics, control, and decision-making run as separate nodes.
order: 1
thumb: /assets/img/projects/brickbot/cover.png
preview: /assets/video/previews/brickbot-drops.mp4   # plays on the home-page card while hovered
hero_video: /assets/video/brickbot/drops.mp4
hero_poster: /assets/video/brickbot/drops.jpg
hero_portrait: true
hero_side: true
hero_caption: "Five drops in a row. The robot catches the three it can reach in time and skips the other two. Drops 1 and 2 are the same spot, but from 5 m there isn't enough fall time to get there."
timeline: Oct 2026
tags: [ROS 2, Python, URDF, tf2, Automated testing]
results:
  - "**Catch or skip?** The robot decides from the brick's fall time vs. how far it can drive in that time"
  - "**Odometry-based control:** the controller never sees the robot's true position. It estimates it from wheel angles and drives at 100 Hz"
  - "**Automated tests:** unit tests for the physics + launch tests that drop a brick and verify that it lands, slides off, and freezes in space"
---

The second project in the class, after [Closed-Loop Waypoint Tracking](/projects/ros2-waypoint-follower/). This time the robot, the physics, and the visuals were all mine to build.

## System

- **simulation:** the "mock hardware." It's the only node that knows where the robot and brick really are. It steps the physics at 100 Hz, publishes the wheel and platform joint angles, and offers `place` and `drop` services for the brick
- **control:** turns wheel angles into a position estimate (odometry), then drives toward goal poses. It only accepts goals in the world frame and converts them through tf
- **catcher:** watches the brick through tf, decides whether a falling brick is catchable, sends the robot under it, and tilts the platform to dump it
- **physics module:** plain Python with no ROS in it, that way the falling and sliding math can be unit tested on its own

## Catching

When the brick starts falling, the catcher has one shot at the decision. The time to fall to the platform is t = √(2(z − h)/g), and in that time the robot can drive 95% of its top speed × t. If that covers the distance to the brick (within half a platform), it goes for it! Otherwise it shows **Unreachable** and stays still. A small state machine handles the rest: waiting -> catching -> dumping -> waiting.

<div class="demo-grid">
  <div class="demo">
    <a class="demo-media-link" href="/assets/img/projects/brickbot/unreachable.png"><img class="demo-media" src="/assets/img/projects/brickbot/unreachable.png" alt="RViz showing the robot far from a brick on the ground, with an Unreachable label in the air"></a>
    <div class="demo-text"><h3>Out of reach</h3><p>The brick lands too far away for the robot to get there in time, so it doesn't bother to try.</p></div>
  </div>
  <div class="demo">
    <div class="demo-media slideshow" data-interval="3000">
      <a class="slide is-active" href="/assets/img/projects/brickbot/big-robot-zero.png" data-label="big_robot.yaml"><img src="/assets/img/projects/brickbot/big-robot-zero.png" alt="The larger robot configuration in RViz next to the joint state sliders, all at zero"></a>
      <a class="slide" href="/assets/img/projects/brickbot/big-robot-moved.png" data-label="Moving the joints"><img src="/assets/img/projects/brickbot/big-robot-moved.png" alt="The larger robot with the platform tilted, stem turned, and wheel rotated using the joint state sliders"></a>
    </div>
    <div class="demo-text"><h3>Same code, bigger robot</h3><p>Platform height, size, wheel radius, and top speed live in one YAML file. The URDF and every node read it, so swapping in <code>big_robot.yaml</code> changes everything at once. The sliders move the platform tilt (alpha), steering (theta), and wheel (phi).</p></div>
  </div>
</div>

## Robot Model

- **URDF in xacro:** a platform on a tilting hinge (alpha), a steering stem (theta), and a wheel (phi), built with a reusable link macro
- **tf tree:** world -> odom (where the robot started) -> base_link (the odometry estimate) -> stem -> wheel, plus world -> brick
- **RViz:** the arena walls and brick are drawn with markers, and the robot model updates live from the joint states

## Testing

`colcon test` runs style checks, unit tests for the physics (driving, free fall, and sliding down a tilted platform), and two launch tests that start the real nodes. One checks that control publishes at 100 Hz, and the other drops a brick, tilts the platform, and checks that the brick lands, slides off the edge, and stays where it stopped.
