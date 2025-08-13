---
layout: post
title: Pediatric Prosthetic Foot
description: Engineered a low-cost, durable pediatric prosthetic leg that adapts to growth, integrating mechanical design with real-time gait tracking.
skills:
  - Mechanical Design
  - Computer Vision
  - Team Leadership
main-image: /foot-cover.png
---

## Overview

Led a team of five in the engineering design and testing of a low-cost pediatric prosthetic leg for our senior capstone project at UCLA. The device was engineered to mimic natural gait biomechanics while allowing easy adjustability as the child grows.

## Design and Development Process

Data from the gait cycle of a 7-year-old and an adult was scaled by interpolation to approximate the torque vs. angle graph of children from 9 to 12 years old, with their for each year approximated by growth charts depending on their initial weight at 9 years old. MATLAB was used to create an interface that allowed us to adjust the weights to get the desired torque curves for our optimization. From here, we fine-tuned the parameters until we achieved normal gait cycles.

![Torque-Angle Curve](/torque-angle-curve.png)

![Torque-calculations](/Torque-calculations.png)
## Key Variables
- **$L_0$**: Free length of the spring
- **$L_s$**: Length of the spring
- **$\theta$**: Angle that the pylon is tilted forward from equilibrium

***

The following calculations were done in order to determine the torque contribution from each spring in our system. The initial angle between $l$ and $r$, $\alpha_0$ can be found using the law of cosines:

$$\alpha_0 = \cos^{-1}\left(\frac{1}{2rl}(r^2 + l^2 - L_{s,\theta=0})\right)$$

This could be used to find the angle, $\alpha$, in terms of theta:

$$\alpha(\theta) = \alpha_0 - \theta$$

Inverting the law of cosines to then solve for the length of the spring, we get:

$$L_s(\theta) = \sqrt{r^2 + l^2 - 2rl \cos(\alpha(\theta))}$$

We used Hooke’s Law to turn this value into force and then calculated theta given that force and lever arm:

$$F_s(\theta) = -k(L_s(\theta) - L_0)$$

$$\tau(\theta) = |F(\theta)||r|\sin(\beta(\theta))$$

, where $\sin(\beta(\theta)) = \frac{l}{L_s}\sin(\alpha(\theta))$.

In our three-spring design, the torques are added up in order to get the total torque provided by our system:

$$\tau_{\text{tot}}(\theta) = \sum_{n=1}^{N} \tau_{n}(\theta)\Pi$$

, where $N$ is the number of springs and $\Pi = \{1, \text{ if the spring is in front of the ankle}; -1 \text{ if the spring is behind the ankle}\}$.

Finite Element Analysis was done using SoldWorks in order to verify material selection. Manufacturing was done using CNC machining, water-jetting and hand-machining - such as lathes, mills, and bench drills.

Functionally, the prosthetic foot operates with a hinge joint that allows the top foot plate to rotate relative to the pylon during the gait cycle. As the foot plate moves, it is initially compressed by the posterior and first anterior springs to provide a baseline level of stability. The most anterior spring is position-adjustable using a thumb screw to tune the overall stiffness according to the child’s weight. Pre-drilled holes, determined via calculations, allow for this adjustment. Notably, this spring is positioned slightly lower than the other two to generate greater torque once the ankle reaches a critical angle, mimicking the torque-angle relationship observed in normal human gait.

## Key Contributions

- Designed and modeled the full prosthetic assembly using SolidWorks and MATLAB.
- Developed a real-time computer vision pipeline to track gait behavior and detect when springs should be replaced to support growing children.
- Conducted iterative prototyping and mechanical testing to evaluate durability and performance.
- Managed procurement, timeline, and team coordination throughout the lifecycle.

## Outcome

- Built a functional prototype under budget (<$200).
- Presented at UCLA's Engineering Design Showcase.
- Recognized for integrating low-cost biomechanics with modern sensing for pediatric care.


