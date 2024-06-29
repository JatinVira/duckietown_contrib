# Computing

---

[Back to Index](README.md) | [Next: Power](power.md)

## Computing - Introduction

What is Computing? And Why do we need an onboard computer in a robot?

Computing in robotics involves the processing of data, decision-making, and control. 
It is the brain of a robot, handling everything from sensor data processing to executing complex algorithms for navigation and interaction.

In the context of robotics, computing systems are responsible for:

- Interpreting data from sensors and making decisions based on that data.
- Controlling actuators to perform desired actions.
- Running software that allows the robot to execute tasks autonomously.

Let's take a simple example from our real world.
Imagine you are driving a car using GPS navigation. 
Your brain processes information from the GPS, road signs, and your surroundings to make decisions about where to go and how to drive. 
In this scenario, your brain acts as the computing unit that integrates all the data and controls your actions.

In robotics, computing systems perform similar functions, enabling the robot to understand its environment, make decisions, and interact with its surroundings.

Let's proceed to understand the computing components equipped on the Duckiebot DB21J robot.

---

### Jetson Nano

#### Description

The Jetson Nano is a powerful computing module designed by NVIDIA, specifically for AI and robotics applications.
The Duckiebot DB21J is equipped with a Jetson Nano, providing it with the computational power required for advanced tasks.

#### Picture

<div align="center">
<img src="images/jetson_nano.jpg" alt="Jetson Nano Picture">
</div>

#### Working Principle

The Jetson Nano operates as the central processing unit (CPU) of the Duckiebot, managing all computational tasks. 

It processes data from various sensors, runs algorithms for navigation and control, and executes the software that drives the robot's behavior. 

With its quad-core ARM CPU and 128-core NVIDIA GPU, the Jetson Nano can handle complex computations, including real-time image processing and machine learning inference.

#### Usage Example

The Jetson Nano enhances the Duckiebot's capabilities by providing robust computational power for various tasks:

- Processing sensor data to understand the environment and make decisions.
- Running machine learning models for tasks such as object detection and path planning.
- Controlling actuators to perform precise movements and interactions.

With the Jetson Nano, we can leverage advanced computing techniques to:

- Implement real-time navigation and obstacle avoidance.
- Execute complex algorithms for autonomous driving and task execution.
- Integrate with other systems for comprehensive data processing and decision-making.

[Back to Index](README.md) | [Next: Power](power.md)

---
