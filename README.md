This is a copy of the [original repository](https://github.com/Drew-Robotics/offseason-2024) off of the github page for the FRC robotics team I'm on (#8852). I wanted to keep this description I'm writing here off of the page that represents the whole team.

## Tools Used
Java, gradle, wpilib, PhotonVision, PathPlanner, and various vendor libraries to interact with hardware on the robot (rev robotics, kauai labs, playing with fusion, and others).
Also tools to control the robot and read data like Shuffleboard and AdvantageScope.

## Work Split
This was a collaboration with the [other programmer on the team](https://github.com/Pickles888), who implemented some older features from the 2024 on-season robot as an exercise, as well as some early versions of the intake and feeder subsystems. The areas I'm highlighting are parts that I had exclusively worked on.

## Vision

Last year was our first robot that employed cameras and made use of vision tools like photon vision. The goal is to be able to read data from four different cameras with known positions relative to the robot, detect april tags (they look like small QR codes) also with known positions relative to the field, to try and work backwards to find the position of the robot relative to the field. We made use of black and white cameras from Arducam, and two Orange Pi's running PhotonVision. We had to set up a custom field at the school where we're located which is why all the april tags have random looking hardcoded positions.

## Drivetrain

For the past year or so we've been working on swerve drive robots, a type of drivetrain where for each "module" there is a motor to spin a wheel, and another to orient it. Enough of these modules results in a type of drive called holonomic drive, where regardless of position and orientation, the robot can be sent off in any direction, allowing for some really interesting and complex maneuvers while moving the robot. This isn't the first swerve drive subsystem I've written but when writing this version there was a major focus on readability, organization, maintainability, and personalization to our team. It was my first time working on a swerve drive with another person, so this wasn't just a coding project, but a teaching project as well, one of the reasons why I wanted this to be as readable as possible. I also created a smaller [Python demo](https://github.com/njbizzle/SwerveDriveDemo) right at the start of the project to show the math behind the swerve drive.

