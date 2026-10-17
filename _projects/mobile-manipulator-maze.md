---
title: Mobile Manipulator Maze Challenge
context: Robotics Final Project · Santa Clara University
summary: An AgileX LIMO Cobot, a mobile base with a 6-DOF arm, that drives through a block maze, picks up socks, and drops them on QR-code targets with no teleoperation.
order: 5
thumb: /assets/img/projects/maze/arm-maze.jpg
hero_side: true
hero_slides_ratio: 1 / 1
hero_slides:
  - src: /assets/img/projects/maze/arm-maze.jpg
    label: In the maze
    alt: LIMO Cobot with its arm raised inside the block maze
  - src: /assets/img/projects/maze/arm-grasp.jpg
    label: Reaching for a sock
    alt: The arm extended over the maze wall
  - src: /assets/img/projects/maze/rviz-joints.jpg
    label: Tuning poses in RViz
    alt: RViz model of the LIMO Cobot with joint sliders
  - src: /assets/img/projects/maze/maze-top.jpg
    label: The maze
    alt: Top-down view of the block maze with QR-code targets
  - src: /assets/img/projects/maze/team-tuning.jpg
    label: Testing on the floor
    alt: The team testing the robot in the maze
hero_caption: The LIMO Cobot in the course maze, and the arm poses we tuned in RViz.
team: ["Armon Choudhry"]
tags: [ROS, MoveIt, Python, RViz]
results:
  - "**Reached 3 of 4 QR targets**, delivered one sock, and contacted a second"
  - "**Tied for the highest score** in the course section"
  - "**No teleoperation:** the run went start to finish on real hardware with no one at the controls"
---

## How It Worked

- **Robot:** an AgileX LIMO Cobot, a small mobile base carrying a 6-DOF myCobot arm, with LiDAR and a depth camera onboard, running ROS
- **Navigation:** Python ROS nodes published a hardcoded sequence of velocity commands to drive each leg of the maze
- **Manipulation:** we tuned arm poses in MoveIt and RViz, then hardcoded them as approach → grasp → retract → place
- **Execution:** one script reset the arm to a safe home pose and another ran the full routine, so resets between attempts were fast

## What Held It Back

We spent a lot of time trying to integrate the LiDAR for mapping and localization, but couldn't get it working reliably before the deadline. That left the run **open-loop**: the robot followed timed commands without knowing where it was, so small amounts of wheel slip or a slightly off starting position built up over the course, which is likely what cost us the fourth target.

Not being able to use the LiDAR or build a map is a big part of why I'm in Northwestern's MSR program now, learning the perception, mapping, and feedback control this robot was missing. My [ROS 2 waypoint follower](/projects/ros2-waypoint-follower/) is a first step: it steers from pose feedback instead of timed commands.
