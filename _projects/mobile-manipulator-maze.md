---
title: Mobile Manipulator Maze Challenge
context: Robotics Final Project · Santa Clara University
summary: A LIMO Pro mobile manipulator that navigates a maze, picks up socks, and places them on QR-code targets autonomously, with no teleoperation.
order: 3
featured: true
thumb: /assets/img/projects/maze/arm-maze.jpg
hero_image: /assets/img/projects/maze/rviz.jpg
role: Navigation and manipulation routines in ROS; arm pose tuning in MoveIt
team: ["Armon Choudhry"]
tags: [ROS, Python, MoveIt, RViz, Ubuntu]
results:
  - "**Reached 3 of 4 QR targets**, grasped and placed one sock, and contacted a second"
  - "**Fully autonomous** execution on real hardware"
  - "**Tied for the highest score** in the course section"
---

## Overview

The robot is an AgileX LIMO Pro base with a 6-DOF arm. The challenge: drive through a block maze, find QR-code targets, and deliver socks to them with no human input once the run starts.

<div class="gallery">
  <figure><img src="/assets/img/projects/maze/maze.jpg" alt="Maze layout from above"></figure>
  <figure><img src="/assets/img/projects/maze/arm-grasp.jpg" alt="Arm grasping in the maze"></figure>
</div>

## Software

### Navigation

- ROS nodes in Python publish **velocity commands** to the mobile base
- Base positioning was refined so each grasp starts from a repeatable pose

### Manipulation

- **MoveIt + RViz** were used to visualize frames and end-effector motion
- Joint-space poses were tuned for collision-free grasping and placement
- Each pick follows a fixed sequence: **approach → grasp → retract → place**

### Execution

Autonomy was split into two scripts: one returns the arm to a safe home pose, and the other runs the full navigation-and-manipulation routine. This made resets fast and the runs repeatable on hardware.

## Results

The robot reached three of the four QR targets, placed one sock and contacted a second, and tied for the highest score in the section.
