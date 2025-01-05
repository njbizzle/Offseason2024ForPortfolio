# First Robotics Competition Offseason 2024 Codebase

#### This is the codebase for our most recent FRC robot. Notable capabilities are vision and position estimation, the drivetrain, and the LED tools.

This is a copy of the [original repository](https://github.com/Drew-Robotics/offseason-2024) off of the github page for the FRC robotics team I'm on (#8852). I wanted to keep this description separate from the page representing the entire team.

## Overview

This is the most recent repository for FRC team 8852, which I worked on as lead programmer. I was the main person managing this repository but there were other people who wrote sections. One of the main features that I worked on was the implementation of a swerve drivetrain, which this season especially was designed to integrate easily into our autonomous pathing and vision software. Vision was another large undertaking for the offseason. I worked on writing the vision subsystem and camera classes, as well as configuring the hardware and firmware, all of which works together to build an estimation of our robot's position. Addidionally, the LED system is new on this project. I built up tools to quickly make and manage different patterns to help convey the status of our robot from far away (also they look really cool).

## Tools Used

Java, gradle, wpilib, PhotonVision, PathPlanner, and various vendor libraries to interact with hardware on the robot (rev robotics, kauai labs, playing with fusion, and others).
Also tools to control the robot and read data like Shuffleboard and AdvantageScope.

## Work Split

This was a collaboration with the [other programmer on the team](https://github.com/Pickles888), who is in the process of reimplementing autonomous driving from the 2024 on-season robot. They had also written some early versions of the intake and feeder subsystems. The sections highlighted here are the parts I worked on exclusively.

## Vision

Last year was our first robot that employed cameras and made use of vision tools like PhotonVision. The goal is to be able to read data from four different cameras with known positions relative to the robot, detect AprilTags (which look like small QR codes) also with known positions relative to the field, to try and work backwards to find the position of the robot relative to the field. We made use of black and white cameras from Arducam and two Orange Pi's running PhotonVision. We had to set up a custom field at the school where we're located, then measured out and hardcoded positions for the AprilTags.

## Drivetrain

For the past year or so we've been working on swerve drive robots, a type of drivetrain where for each "module" there is a motor to spin a wheel, and another to orient it. Enough of these modules results in a type of drive called holonomic drive, where regardless of position and orientation, the robot can be sent off in any direction, allowing for some really interesting and complex maneuvers while moving the robot. This isn't the first swerve drive subsystem I've written but when writing this version there was a major focus on readability, organization, maintainability, and personalization to our team. It was my first time teaching the concepts of swerve drive, making this not just a coding project but also a teaching one, one of the reasons why I wanted this to be as readable as possible. I also created a smaller [Python demo](https://github.com/njbizzle/SwerveDriveDemo) right at the start of the project to show the math behind the swerve drive.

### Some Images From the Swerve Math Demo

#### Example With 4 Modules (I've never seen a team that doesn't do 4 modules)
<img src="pictures/Figure_1.png">

#### Example With 8 Modules (It's cool to see and it demonstrates how general the math is)
<img src="pictures/Figure_3.png">

## LED System

I got pretty annoyed trying to use other people's LED code. CTRE (the company that made all LED hardware) had a limited system for managing what patterns were being sent to the LEDs. I wrote some code to manage different patterns, states, mix patterns, transition between patterns, and a few other tools. I ended up really enjoying it as a design project, and it turned out really well. Patterns are described with a function that takes in variables like time, progress through the defined LED strip, and a few other factors that can be set up, then you just need to return a color. It makes it super simple to describe patterns mathematically.

This existed in some form on our on-season robot, and it made it really easy to convey the state of the robot from really far away. Overall it's a super generally applicable tool and I'm really happy with how it turned out.

Here's an older example pattern.

[![](https://img.youtube.com/vi/YQFC4AxMUEw/0.jpg)](https://www.youtube.com/watch?v=YQFC4AxMUEw)

We also made use of these tools to have the LED strip indicate where the cameras detected a vision target to be. It illuminated the LEDS that were in the direction of the target, and the number of LEDs illuminated corresponded to the target distance. I don't really have an easy way to set that up again and sadly I never documented it, but it was a fun project that employed this tool that I wanted to mention.
