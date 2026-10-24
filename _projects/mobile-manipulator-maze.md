---
title: Mobile Manipulator Maze Challenge
context: Robotics Final Project · Santa Clara University
summary: A mobile robot with a 6-DOF arm that drives through a block maze, picks up socks, and drops them on QR-code targets with no teleoperation.
order: 6
thumb: /assets/img/projects/maze/thumb.jpg
hero_side: true
hero_slides_ratio: 1 / 1
hero_slides_interval: 2600
hero_slides:
  - src: /assets/img/projects/maze/run-1.jpg
    label: Run · 1
    alt: Still from the scored run in the maze
  - src: /assets/img/projects/maze/run-2.jpg
    label: Run · 2
    alt: Still from the scored run in the maze
  - src: /assets/img/projects/maze/run-3.jpg
    label: Run · 3
    alt: Still from the scored run in the maze
  - src: /assets/img/projects/maze/run-4.jpg
    label: Run · 4
    alt: Still from the scored run in the maze
  - src: /assets/img/projects/maze/run-5.jpg
    label: Run · 5
    alt: Still from the scored run in the maze
  - src: /assets/img/projects/maze/run-6.jpg
    label: Run · 6
    alt: Still from the scored run in the maze
  - src: /assets/img/projects/maze/run-7.jpg
    label: Run · 7
    alt: Still from the scored run in the maze
  - src: /assets/img/projects/maze/run-8.jpg
    label: Run · 8
    alt: Still from the scored run in the maze
  - src: /assets/img/projects/maze/run-9.jpg
    label: Run · 9
    alt: Still from the scored run in the maze
hero_caption: "Stills from the scored run, sharpened from phone video. Near the end the gripper reaches the last sock but can't hold it."
team: ["Armon Choudhry"]
tags: [ROS, MoveIt, Python, Mobile manipulation]
results:
  - "**Reached 3 of 4 QR targets** and delivered one sock. The gripper reached a second but couldn't hold it before time ran out"
  - "**Tied for the highest score** in the course section"
  - "**No teleoperation:** the run went start to finish on real hardware with no one at the controls"
---

## How It Worked

<div class="split" markdown="1">
<div markdown="1">

- **Robot:** an AgileX LIMO Cobot: a LIMO Pro base on **mecanum wheels** (so it can strafe sideways) carrying a 6-DOF myCobot arm, with LiDAR and a depth camera onboard, running ROS
- **Navigation:** Python ROS nodes published a hardcoded sequence of velocity commands to drive each leg of the maze
- **Manipulation:** we tuned arm poses with joint sliders in RViz and MoveIt, then hardcoded them as approach → grasp → retract → place
- **Execution:** one script reset the arm to a safe home pose and another ran the full routine, so resets between attempts were fast

</div>
<div class="demo-media slideshow" style="aspect-ratio: 3 / 4">
  <a class="slide slide--contain is-active" href="/assets/img/projects/maze/robot.jpg" data-label="LIMO Cobot"><img src="/assets/img/projects/maze/robot.jpg" alt="The LIMO Cobot: mecanum-wheeled base with a depth camera and a white 6-DOF arm"></a>
  <a class="slide slide--contain" href="/assets/img/projects/maze/rviz-sliders.jpg" data-label="Tuning joints in RViz"><img src="/assets/img/projects/maze/rviz-sliders.jpg" alt="RViz joint_state_publisher sliders used to tune arm poses"></a>
  <a class="slide slide--contain" href="/assets/img/projects/maze/maze-top.jpg" data-label="The maze"><img src="/assets/img/projects/maze/maze-top.jpg" alt="Top-down view of the block maze"></a>
</div>
</div>

## What Held It Back

We spent a lot of time trying to integrate the LiDAR for mapping and localization, but couldn't get it working reliably before the deadline. That left the run **open-loop**: the robot followed timed commands without knowing where it was, so small errors and a slightly off starting position built up over the course. Every leg had to be hand-tuned by trial and error, and that tuning time is a big part of why we ran out of time before the fourth target.

Not being able to use the LiDAR or build a map is a big part of why I'm in Northwestern's MSR program now, learning the perception, mapping, and feedback control this robot was missing. My [closed-loop waypoint tracking project](/projects/ros2-waypoint-follower/) is a first step: it steers from pose feedback instead of timed commands.
