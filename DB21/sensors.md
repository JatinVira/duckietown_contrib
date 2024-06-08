# Sensors

---

[Back to Index](README.md) | [Next: Actuators](actuators.md)

## Sensors - Introduction

What are Sensors? And why do we need them?

Sensors are devices that detect and respond to some type of input from the physical environment.
They convert the physical quantity into an electrical signal that can be read by an observer or by an instrument.

In the context of robotics, sensors are used to perceive the environment and provide feedback to the robot.
They help the robot to understand its surroundings, make decisions, and interact with the environment.

Let's take a simple example from our real world.
Imagine that you are walking in a dark room and you want to find the light switch.
You use your sense of touch to feel the wall and find the switch.
In this example, your sense of touch is acting as a sensor that helps you to perceive the environment and interact with it.

Let's proceed to understand the various sensors equipped on the Duckiebot DB21 robot.

---

## Sensors on Duckiebot DB21

### Camera

#### Description

The Duckiebot DB21 is equipped with a Waveshare Raspberry Pi Camera Module with a fish-eye lens, providing a wide 160-degree field of view. This high-quality camera is crucial for capturing detailed images of the robot's environment, which are then used for various computer vision tasks.

#### Picture

<div align="center">
<img src="images/camera.jpg" alt="Camera Picture">
</div>

#### Working Principle

1. Gathering Light and focusing it on a Sensor:

    Light from the environment reflects off objects and travels towards the camera. 
    The lens focuses this incoming light to create a sharp image on the sensor plane.

    <div align="center">
    <img src="images/lens_focusing.jpg" alt="Lens Focusing Light">
    </div>

2. Capturing Light with Photodetectors:

    The digital sensor behind the lens is an array of millions of tiny photodetectors, typically made of CMOS (Complementary Metal-Oxide-Semiconductor) technology. 
    Each photodetector acts like a tiny light meter, converting the captured light into an electrical signal.

3. Converting Light Intensity to Digital Values:
   
   The strength of the electrical signal from each photodetector depends on the amount of light it receives. 
   This translates directly to the brightness level of that specific point in the image. 
   The camera then assigns a digital value to each signal, typically ranging from 0 (black, no light detected) to a maximum value (often 255, white, maximum light detected).
   The color of each pixel is determined by the intensity of the red, green, and blue light detected by the sensor.

4. Assembling the Image:

    The camera arranges the millions of individual pixel values into a grid, creating a digital representation of the scene.

    <div align="center">
    <img src="images/assembling_an_image.png" alt="Assembling an Image">
    </div>
    

#### Functionality

The camera captures images (frames) of the surrounding environment.
These images are processed by the robot to understand its surroundings and make autonomous decisions.
The camera enables the Duckiebot DB21 to:

- Detect and follow lanes on the road
- Identify and react to traffic signs and obstacles
- Navigate complex environments using simultaneous localization and mapping (SLAM)

#### Usage Example

The continuous stream of images from the camera can be utilized for real-time navigation.
For instance, the Duckiebot DB21 can:

- Use detected lines on the road to maintain a straight path or navigate curves.
- Apply feature detection to recognize specific patterns or objects in its environment.
- Build control points from the visual data to plot a course and adjust its movements accordingly.


---

### ToF Sensor

#### Description

The Duckiebot DB21 is equipped with a VL53L1X ToF sensor.
The ToF sensor gives us a depth data of the environment, which is crucial for obstacle avoidance and navigation.

#### Picture

<div align="center">
<img src="images/tof.jpg" alt="ToF Sensor Picture">
</div>

#### Working Principle

A Time-of-Flight (ToF) sensor works by emitting a short burst of infrared light, invisible to the human eye. 
This light pulse travels outwards and bounces off objects in the environment. 
The sensor then measures the time it takes for the light pulse to travel to an object and reflect back. 
Based on the speed of light and the measured time, the sensor calculates the distance to the object.

#### Functionality

The ToF sensor provides depth information about the environment.
This information is used for obstacle avoidance, navigation, and mapping.
The ToF sensor enables the Duckiebot DB21 to:

- Detect obstacles in its path and avoid collisions
- Measure distances to objects for safe navigation
- Create a 3D map of the environment for localization and path planning
- Assist in docking maneuvers and precise positioning

#### Usage Example

The ToF sensor can be used to detect obstacles in the robot's path.
For instance, the Duckiebot DB21 can:

- Stop or change its course when an obstacle is detected within a certain range.
- Calculate the distance to objects in front of it to avoid collisions.
- Create a depth map of the environment to plan safe and efficient paths.
  
---

