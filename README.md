# First Robotics Competition Offseason 2024 Codebase

#### This is the codebase for our most recent FRC robot. Notable capabilities that I would like to showcase are vision and position estimation, the drivetrain, and the LED tools.

This is a copy of the [original repository](https://github.com/Drew-Robotics/offseason-2024) from the GitHub page for the FRC robotics team that I co-founded (#8852). I wanted to keep this description separate from the page representing the entire team.

## Overview

This project is the most recent repository for FRC team 8852, where my primary role is lead programmer. I managed this repository but there were other people who wrote sections of the code. One of the main features that I worked on was our implementation of a swerve drivetrain, which was specifically designed to integrate easily into our autonomous pathing and vision software. Vision was another large undertaking for the offseason. I worked on writing the vision subsystem and camera classes, as well as configuring the associated hardware and firmware, all of which works together to build an estimation of our robot's position. Additionally, the LED system has been improved. I created tools to quickly create and manage different LED animations to help convey the status of our robot from far away. 

## Tools Used

The language used is Java. The following tools and software packages are also used:

Gradle to build
WPILib for FRC libraries and tools
PhotonVision
PathPlanner
Various vendor libraries to interact with hardware (e.g., Rev Robotics, Kauai Labs, Playing With Fusion among others)
Git/GitHub for version control

Additionally, we used certain tools to control the robot and visualize data such as Shuffleboard and AdvantageScope.

## Work Split

This was a collaboration with [one other programmer on the team](https://github.com/Pickles888), who is in the process of reimplementing autonomous driving from our 2024 on-season robot. They had also written early versions of the intake and feeder subsystems. The sections highlighted in this portfolio are features I worked on exclusively.

## Vision

The 2024 season had our first robot that employed cameras and made use of vision tools like PhotonVision. The goal was to be able to read data from four different cameras with known positions relative to the robot, detect AprilTags (which look like small QR codes) with known positions relative to the field, and to try and work backwards to find the position of the robot relative to the field. We made use of black and white cameras from Arducam and two Orange Pi vision co-processors running PhotonVision. Finally, we set up a custom field at the school and hung up AprilTags to run tests on the position estimation.

## Drivetrain

For the past year we've been working with swerve drive robots, a type of drivetrain where for each "swerve module" there is a motor to spin a wheel, and another to orient it. Enough of these modules operating together results in a type of drivetrain called a holonomic drivetrain, where regardless of position and orientation, the robot can be sent off in any direction. This allows for interesting and complex robot maneuvers and greatly increases our speed in autonomous. I’ve had experience working with swerve drivetrains before, so this specific implementation had a major focus on readability, organization, maintainability, and personalization to our team. Being a collaborative project with team members who weren’t as familiar with swerve drive, I spent a lot of time teaching the concepts, another reason why this repository has such an emphasis on readability. I also created a [Python swerve demo](https://github.com/njbizzle/SwerveDriveDemo) to show the math behind the swerve drive.

### Some Images From the Swerve Math Demo

#### Example With 4 Modules (I've never seen a team that doesn't do 4 modules.)
![](pictures/Figure_1.png)

#### Example With 8 Modules (It's cool to see and it demonstrates how general the math is.)
![](pictures/Figure_3.png)

## LED System

CTRE, the company that makes the LED hardware, had a limited system for managing what patterns were sent to the LED strips. Wanting more flexibility, I wrote code to manage different patterns, states, mix patterns, transition between patterns, as well as a few other features. Patterns are described with a function that takes in variables such as time and position in the LED strip to determine a color. These tools allow patterns to be easily described mathematically.

This existed in some form on our on-season robot and it made it extremely easy to convey the state of the robot from a distance. For example, we made use of these tools to have the LED strip indicate where the cameras detected a vision target. Specifically, it illuminated the LEDS that were in the direction of the target, and the number of LEDs illuminated corresponded to the target distance. I don't have an easy way to set that up again and sadly I didn’t document it, but it was a fun project that employed this tool. Overall it's a generally applicable tool and I'm proud of my design and the final implementation.

Here's an older example pattern. (YouTube link in the image)

[![](https://img.youtube.com/vi/YQFC4AxMUEw/0.jpg)](https://www.youtube.com/watch?v=YQFC4AxMUEw)
