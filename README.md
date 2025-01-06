---
geometry: margin=3cm
colorlinks: true
---

# First Robotics Competition Offseason 2024 Codebase

#### This is the codebase for our most recent FRC robot. Notable capabilities are vision and position estimation, the drivetrain, and the LED tools.

This is a copy of the [original repository](https://github.com/Drew-Robotics/offseason-2024) off of the github page for the FRC robotics team I'm on (#8852). I wanted to keep this description separate from the page representing the entire team.

## Overview

This project is the most recent repository for FRC team 8852, which I work on as lead programmer. I managed this repository but there were other people who wrote sections of the code. One of the main features that I worked on was the implementation of a swerve drivetrain, which was specifically designed to integrate easily into our autonomous pathing and vision software. Vision was another large undertaking for the offseason. I worked on writing the vision subsystem and camera classes, as well as configuring the associated hardware and firmware, all of which works together to build an estimation of our robot's position. Additionally, the LED system is new on this project. I built tools to quickly create and manage different LED patterns to help convey the status of our robot from far away. 

## Tools Used

The language used is Java. The following tools and software packages are also used:

Gradle to build
WPILib for FRC tools
PhotonVision
PathPlanner
Various vendor libraries to interact with hardware (e.g., Rev Robotics, Kauai Labs, Playing With Fusion among others). 

Additionally, we used certain tools to control the robot and visualize data such as Shuffleboard and AdvantageScope.

## Work Split

This was a collaboration with [one other programmer on the team](https://github.com/Pickles888), who is in the process of reimplementing autonomous driving from our 2024 on-season robot. They had also written early versions of the intake and feeder subsystems. The sections highlighted in this portfolio are parts I worked on exclusively.

## Vision

Last year was our first robot that employed cameras and made use of vision tools like PhotonVision. The goal is to be able to read data from four different cameras with known positions relative to the robot, detect AprilTags (which look like small QR codes) also with known positions relative to the field, to try and work backwards to find the position of the robot relative to the field. We made use of black and white cameras from Arducam and two Orange Pi's running PhotonVision. We had to set up a custom field at the school where we're located, then measured out and hardcoded positions for the AprilTags.

## Drivetrain

For the past year or so we've been working on swerve drive robots, a type of drivetrain where for each "module" there is a motor to spin a wheel, and another to orient it. Enough of these modules results in a type of drive called holonomic drive, where regardless of position and orientation, the robot can be sent off in any direction, allowing for some really interesting and complex maneuvers while moving the robot. This isn't the first swerve drive subsystem I've written but when writing this version there was a major focus on readability, organization, maintainability, and personalization to our team. It was my first time teaching the concepts of swerve drive, making this not just a coding project but also a teaching one, one of the reasons why I wanted this to be as readable as possible. I also created a smaller [Python demo](https://github.com/njbizzle/SwerveDriveDemo) right at the start of the project to show the math behind the swerve drive.

### Some Images From the Swerve Math Demo

#### Example With 4 Modules (I've never seen a team that doesn't do 4 modules.)
![](pictures/Figure_1.png)

#### Example With 8 Modules (It's cool to see and it demonstrates how general the math is.)
![](pictures/Figure_3.png)

## LED System

CTRE, the company that makes the LED hardware, had a limited system for managing what patterns were sent to the LED strips. Wanting more flexibility, I wrote code to manage different patterns, states, mix patterns, transition between patterns, as well as a few other features. I ended up enjoying it as a design project and I'm proud of the way it turned out. Patterns are described with a function that takes in variables such as time and position in the LED strip to determine a color. The implementation is an elegant way to describe patterns mathematically.

This existed in some form on our on-season robot and it made it really easy to convey the state of the robot from really far away. Overall it's a generally applicable tool and I'm really happy with how it turned out.

Here's an older example pattern. (YouTube link in the image)

[![](https://img.youtube.com/vi/YQFC4AxMUEw/0.jpg)](https://www.youtube.com/watch?v=YQFC4AxMUEw)

We also made use of these tools to have the LED strip indicate where the cameras detected a vision target to be. It illuminated the LEDS that were in the direction of the target, and the number of LEDs illuminated corresponded to the target distance. I don't really have an easy way to set that up again and sadly I never documented it, but it was a fun project that employed this tool that I wanted to mention.
