[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/Y5lYn2wb)

# a11g-final-submission

**Team Number: 02**

**Team Name: DEEPSLEEP**

| Team Member Name | Email Address           | GitHub Username |
| ---------------- | ----------------------- | --------------- |
| Xiang Ding       | ding1026@seas.upenn.edu | cloveding       |
| Fengyu Wu        | ericwu77@seas.upenn.edu | FengyuWu-77     |

**GitHub Repository URL:**

https://github.com/ese5160/a11g-final-submission-s26-s26-t02-deepsleep.git

## 1. Video Presentation

[https://youtu.be/_p4__K_uR2w?si=LlCgRaO-XmMvHgUX](https://youtu.be/_p4__K_uR2w?si=LlCgRaO-XmMvHgUX)

## 2. Project Summary

● **Device Description**

This project presents a smart art protection frame designed to provide security monitoring, status tracking, and remote information display for artworks. During normal operation, the device continuously monitors the surrounding environment and the condition of the frame, such as changes in temperature and humidity or whether the artwork has been moved, and periodically uploads this information to a cloud service via a wireless connection. When an abnormal condition is detected, the system immediately triggers a security response, which includes capturing a photo of the scene, sending an alert notification to the user, and optionally providing local feedback through indicator lights or a buzzer. A small display integrated into the front of the frame shows basic artwork information, such as the title and artist, which can be updated remotely through the cloud without direct interaction with the device. Designed with ease of use, minimal visual intrusion, and operational reliability in mind, the smart frame maintains essential monitoring and alert functions even when network connectivity or certain features are temporarily unavailable, making it suitable for use in homes, galleries, or exhibition spaces as a modern and intelligent solution for artwork protection.

● **Device Functionality**

● **Challenges**

● **Prototype Learnings**

● **Next Steps & Takeaways**

As an optional feature, the device may include an automatic self-balancing mechanism to maintain horizontal alignment. The frame is suspended by two upper-fixed wires with non-rigid lower connections, allowing limited rotation. An internal movable counterweight shifts the center of mass horizontally, enabling the frame to passively rotate under gravity and settle into a stable, level equilibrium state.

● **Project Links**

https://upenn-eselabs.365.altium.com/designs/A9A2A324-723F-4F3C-BA00-0C47C1A8A398

## 3. Hardware & Software Requirements

### Hardware Requirements Specification (HRS)

| **ID** | **Description**                                                                                                                                                                                                                                                                                                                                                 |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| HRS-01       | An LCD shall be mounted on the picture frame to display textual information including artwork name and author, and the displayed information shall be remotely updatable via cloud communication without interrupting higher-priority security functions.                                                                                                            |
| HRS-02       | A pressure sensor (FSR) shall be used to detect removal of the artwork, and an inertial measurement unit (IMU) to detect movement of the entire picture frame. Either sensor shall trigger an anti-theft event. The IMU shall be capable of measuring roll angle with a resolution of at least 0.5° and an accuracy of at least ±1.0° over a static condition. |
| HRS-03       | Upon detection of theft, the camera MCU shall be triggered to capture at least one image within 1 second, and the captured image shall be transmitted to the cloud and available to the user within 10 seconds of event detection.                                                                                                                                    |
| HRS-04       | Upon detection of theft, a optional visual and/or audible alert should be activated using an LED and/or buzzer to provide immediate feedback.                                                                                                                                                                                                                        |
| HRS-05       | A temperature and humidity sensor shall be used, and environmental data shall be uploaded to the cloud at least once every 2 seconds during normal operation.                                                                                                                                                                                                         |
| HRS-06       | Whether the artwork is present shall be determined based on pressure sensor and IMU data, and the status shall be updated to the cloud at least once every 2 seconds.                                                                                                                                                                                                |
| OPTIONAL     |                                                                                                                                                                                                                                                                                                                                                                       |
| HRS-07       | Automatic Leveling: An automatic leveling mechanism should be used capable of reducing static roll misalignment of the picture frame.                                                                                                                                                                                                                                |
| HRS-08       | The picture frame should be suspended using two flexible cables or wires, with their upper ends fixed on a horizontal line and their lower ends connected to the frame via non-rigid joints.                                                                                                                                                                          |
| HRS-09       | An internal movable mass mechanism should be used to adjust the horizontal position of the overall center of mass of the picture frame.                                                                                                                                                                                                                               |
| HRS-10       | A lead screw–based linear actuation mechanism should be used to convert motor rotation into linear motion for the movable mass.                                                                                                                                                                                                                                      |
| HRS-11       | A stepper motor should be used to drive the lead screw for precise and repeatable positioning of the movable mass.                                                                                                                                                                                                                                                    |

Lead Screw Assembly: The system uses a T8 lead screw with a 2 mm or 4 mm lead and a typical length of 100–200 mm, depending on the frame width. A matching nut is rigidly fixed to the counterweight block and constrained against rotation, allowing only linear translation along the screw. The counterweight block, typically made of metal with a mass in the range of 100–500 g, is mounted on a linear guide slider to ensure smooth motion. A single linear guide rail is sufficient to prevent binding and maintain alignment during operation.

### Software Requirements Specification (SRS)

| **ID** | **Description**                                                                                                                                                                                                                                 |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SRS-01       | LCD Control: The software shall support remote cloud interaction to dynamically update artwork information displayed on the LCD, including the artwork name and artist information.                                                                   |
| SRS-02       | Security Trigger: The system shall capture a photo within 1 second upon a valid trigger event.                                                                                                                                                       |
| SRS-03       | Alarm Response: Upon a trigger event, optional LED and buzzer indicators shall provide immediate local feedback.                                                                                                                                      |
| SRS-04       | Cloud Latency: Alarm notifications and captured images shall be received by the cloud interface within 10 seconds of the event.                                                                                                                      |
| SRS-05       | Environmental Monitoring: During normal operation, the software shall upload temperature and humidity data to the cloud every 2 seconds.                                                                                                             |
| SRS-06       | Presence Detection: The software shall update the artwork presence status to the cloud every 2 seconds using pressure sensor data and IMU motion data.                                                                                               |
| SRS-07       | Risk Assessment: The software shall utilize IMU data to detect high-impact vibrations or sustained tilt in order to evaluate the risk of the frame being shattered or tampered with.                                                                  |
| SRS-08       | Task Scheduling: The software shall implement task scheduling and priority management to ensure that security-related tasks take precedence over non-critical tasks.                                                                                  |
| SRS-09       | Trigger Evaluation Timing Constraint: The software shall evaluate security trigger conditions at a fixed interval of 20 ms and shall generate a valid trigger event only when trigger conditions persist continuously for at least 200 ms.            |
| SRS-10       | Power-On Self-Test (POST): Upon system startup, the software should perform a power-on self-test to verify the operational status of critical software modules and external interfaces before entering normal operation.                              |
| SRS-11       | Degraded Operation Capability: In the event that certain functional modules become unavailable, the software should maintain the minimum required security monitoring and alarm functionality whenever possible rather than halting system operation. |

## 4. Project Photos & Screenshots

## 5. Codebase

Do *not* commit any of your source code to this repository. Rather, provide links to the other GitHub repository you've already been using with your firmware.

- A link to your final embedded C firmware codebases
- A link to your Node-RED dashboard code
- Links to any other software required for the functionality of your device

Link to your final embedded C firmware codebases:
**https://github.com/ese5160/final-project-firmware-s26-t02-deepsleep.git**

Link to your Node-RED dashboard code:
**https://github.com/ese5160/final-project-firmware-s26-t02-deepsleep/blob/main/Node-RED/flows.json**
