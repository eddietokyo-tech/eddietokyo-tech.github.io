---
layout: post
title: 5DOF Robotic Arm
description: Designed, prototyped, and programmed a five-degree-of-freedom robotic arm with inverse kinematics, trajectory planning, and real-time control.
skills:
  - SolidWorks
  - Python
  - Arduino
  - Matlab
  - Robotics Kinematics
main-image: /Robot-arm-CAD.png
---

## Overview

This project involved the design and development of a 5DOF robotic arm capable of executing controlled joint and task-space movements. The system was intended as a low-cost platform for exploring robotic kinematics, inverse dynamics, and physical interaction through external interfaces.


## **BUTTER-PASSING**
***
### 1. Introduction
The purpose of this project was to design and control a robotic manipulator capable of a simple but precise task: passing the butter. This robot was designed to meet the functional requirement of reaching out and passing butter within a constrained environment, with a focus on design efficiency and kinematic accuracy. The robot arm has **5 degrees of freedom (DOF)**, with Dynamixel MX-28AR servo motors acting as actuators.

The project's challenge was in the mechanical design and actuator selection, as well as deriving and implementing the **kinematic equations** for precise arm movement. **Forward and inverse kinematics** were central to this task, as they determine the positional control of the manipulator. The team aimed to explore the complexities of robotic manipulation, from theoretical concepts to practical implementation.

### 2. Robot Design
#### 2.1 Robot Structure
The designed manipulator is a 5-DOF robot arm with four revolute joints and a prismatic joint. This configuration provides enough degrees of freedom to achieve the necessary range of motion to interact with objects at varying distances within a specified workspace. The gripper/end effector is powered by an SG90s micro servo, which is controlled by an Arduino Uno.

{% include image-gallery.html images="Robot-arm-CAD2.png" height="400" %} 


#### 2.2 Workspace Analysis
Initially, the robot's workspace was a hemispherical region with a 30 cm radius. To overcome this limitation, a **linear guide** was integrated to enable linear motion, significantly expanding the robot's operational range and allowing it to serve a larger area. This enhancement demonstrates how a simple mechanical addition can significantly expand a robot's capabilities. 

{% include image-gallery.html images="Workspace.png" height="400" %} 

#### 2.3 Link Length and Joint Configuration
The link lengths were constrained by motor torque capabilities and physical interference. The joints are as follows:
* **Moving Base (Joint 1)**: Prismatic joint; increases reachable workspace.
* **Pivot (Joint 2)**: Revolute joint; controls rotation in the x-y plane.
* **Shoulder (Joint 3)**: Revolute joint; controls ascent, descent, and extension.
* **Elbow (Joint 4)**: Revolute joint; controls ascent, descent, and extension.
* **Wrist (Joint 5)**: Revolute joint; orients the manipulator perpendicular to the surface.
* **End-Effector**: A gripper controlled by an Arduino Uno.

#### 2.4 Design Challenges
A **rack and pinion mechanism** was used to control the gripper. A key issue encountered was adjusting for **3D printer tolerance**, as printing a gear required a tighter tolerance than normal. The team also had to increase the overall robustness of the design by bridging arm linkages and enlarging the baseplate, as it moved too much during operation.

### 3. Static Force Analysis
A **static simulation using SolidWorks FEA** was performed to evaluate the structural integrity of the robotic arm under a load. A downward force of **0.5 N**, which corresponds to the weight of a **50g butter block**, was applied to the gripper. 
The analysis showed that the highest stress was concentrated in the pivot above motor 2 and below motor 3. However, the point of highest deformation was still below the material's yield strength, suggesting that the current pivot design is robust enough. It was determined that the robot could easily pick up a 50g block of butter.

### 4. Forward Kinematics
The **Denavit-Hartenberg (DH) parameter** was used for forward kinematics. The z-axis of motor 3 was deliberately rotated by 180 degrees to maintain the arm's symmetry, canceling out offsets and enhancing performance.

### 5. Inverse Kinematics
Inverse kinematics is the mathematical process of determining the joint angles needed to achieve a specific position and orientation of the end-effector. A **geometric method** was used to solve for the joint angles. The calculations for each joint are performed sequentially:
* **Joint 1 ($\theta_1$)**: Calculated using the projected end-effector position on a 2D plane: $\theta_1 = \operatorname{atan2}(y, x)$.
* **Joints 2 and 3 ($\theta_2$ and $\theta_3$)**: Calculated using a combination of trigonometric equations and the law of cosines. The equations for these are:
    $$\cos(\theta_3) = \frac{r_4^2 - l_2^2 - l_3^2}{2l_2l_3}$$  
    $$\theta_2 = \alpha + \beta - \frac{\pi}{2}$$  
* **Joint 4 ($\theta_4$)**: Controls the orientation of the end-effector and is computed based on the required orientation and the sum of previous joint angles: $\theta_4 = \gamma - \theta_2 - \frac{\pi}{2} + \theta_3$ .

{% include image-gallery.html images="Inverse-kinematics.png" height="400" %} 

### 6. Software Overview
All software was developed in **MATLAB**. An interface was created with the Dynamixel SDK to send joint angle commands, read motor feedback, and adjust settings. The SG90s micro servo for the gripper was controlled separately by an Arduino board.

The control software had **two operating modes**:
1. **Predetermined Trajectory Mode**: The user sets end-effector coordinates, and the software computes inverse kinematics to control the robot's movement. The robot's real-time configuration is plotted using forward kinematics.
2. **User Manual Control Mode**: The user uses a keyboard to change the end-effector's desired position and control the gripper. Inverse kinematics is then used to compute the necessary joint angles in real time.

### 7. Simulation
Simulations were performed through **MATLAB plots** to determine the reachable workspace for a specific end-effector orientation and to test specified coordinates. Physical constraints on the link shape were also applied as limits for joint angles in the simulation.


### 8. Conclusion
The Butter Robot project successfully demonstrates the feasibility of applying robotic systems to small-scale tasks like passing butter using a **5-DOF manipulator**. The project created a functional robotic arm that meets the objective of efficiently delivering butter and stands as an excellent solution for educational purposes and low-cost prototyping.

{% include image-gallery.html images="butter-passing.png" height="400" %} 

## Key Contributions

- Modeled the full robotic arm using SolidWorks, optimizing link lengths and joint spacing using MATLAB-based cost functions.
- Programmed inverse kinematics and Jacobian-based motion in Python and Arduino, including singularity detection and avoidance.
- Simulated robotic motion and torque requirements; tested joint responsiveness using servo motors.
- Integrated custom control inputs including gloves and button interfaces for user interaction.
- Rapid prototyped components using 3D printing for real-world testing and iteration.

## Outcome

- Demonstrated joint and Cartesian control across all 6 degrees of freedom.
- Built a simulation-to-physical testing pipeline using Python + Arduino + 3D-printed hardware.
- Applied theoretical robotics concepts to a hands-on design and control challenge.


