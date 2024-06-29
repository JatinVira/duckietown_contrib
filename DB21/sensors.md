# Sensors

---

[Back to Index](README.md) | [Next: Actuators](actuators.md)

## Sensors - Introduction

What are sensors?  
And why do we need them?

Sensors are devices that detect and respond to some type of input from the physical environment.  
They convert the physical quantity into an electrical signal that can be read by an observer or by an instrument.

In the context of robotics, sensors are used to perceive the environment and provide feedback to the robot.  
They help the robot to understand its surroundings, make decisions, and interact with the environment.

Let's take a simple example from our real world.  
Imagine that you are walking in a dark room and you want to find the light switch.  
You use your sense of touch to feel the wall and find the switch.  
In this example, your sense of touch is acting as a sensor that helps you to perceive the environment and interact with it.

Let's proceed to understand the various sensors equipped on the Duckiebot DB21J robot.

---

## Sensors on Duckiebot DB21J

### Camera

#### Description

The Duckiebot DB21J is equipped with a Waveshare Raspberry Pi Camera Module with a fish-eye lens, providing a wide 160-degree field of view.

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
    

#### Usage Example

The camera captures images (frames) of the surrounding environment. 
Each frame is a 2D array of pixel values, representing the brightness and color of each point in the image.
We can process these frames to extract useful information about the environment.
For example, we can obtain the following information from these frames:

- Region of interest to narrow down the search area
- Grouping a cluster of pixels as edges, lines, etc.
- Detecting patterns, shapes, and objects using these clusters

Once we have this information, we can use it to make decisions and control the robot.
For example, we can:

- Detect lane markings on the road to follow a path, curve, or intersection.
- Identify obstacles in the robot's path to avoid collisions.
- Recognize traffic signs and signals to obey traffic rules.
- Track objects of interest for interaction or navigation.

---

### ToF Sensor

#### Description

The term ToF stands for Time-of-Flight.  
The Duckiebot DB21J is equipped with a VL53L1X ToF sensor.  
The ToF sensor gives us a depth data in front of the robot for a diagonal field of view of 27 degrees.

#### Picture

<div align="center">
<img src="images/tof.jpg" alt="ToF Sensor Picture">
</div>

#### Working Principle

1. Emitting and Receiving Light:
   
    The sensor works by emitting a short burst of infrared light, invisible to the human eye.  
    The spectrum of emitted light is carefully chosen to avoid interference from ambient light sources.  
    The emitted light travels through the air and reflects off objects in the environment.
    
2. Indirect Measurement of Distance:
   
    Since the speed of light is extremely fast, the sensor would have a hard time measuring the time it takes for the light to travel to the object and back (time could be in nanoseconds).   
    Instead, the sensor measures the time it takes for the light to travel to the object and back by comparing the phase of the emitted light with the phase of the received light.  
    This phase shift is directly proportional to the distance between the sensor and the object.

    <div align="center">
    <img src="images/tof_working_principle.png" alt="ToF Sensor Working Principle">
    </div

3. Obtaining Distance Data:

    The sensor uses the phase shift to calculate the distance to the object based on the speed of light.  
    The distance is then converted into a digital value, typically in millimeters or centimeters, and sent as a sensor reading.


#### Usage Example

The robot is practically blind for distance measurement given that a Monocular Camera (single camera) cannot provide depth information.
This is why we have a ToF sensor which provides depth information about the environment in front of the robot.
This data is usually represented in a floating-point number, indicating the distance in meters from the sensor to the object.
We can use this depth information to:

- Detect obstacles in the robot's path and avoid collisions.
- Measure the distance to objects for navigation and interaction.
- Dock the robot accurately to a charging station or a specific location.
  
---

### IMU

#### Description

IMU stands for Inertial Measurement Unit.  
The Duckiebot DB21J is equipped with an MPU-6050 IMU sensor.  
The IMU sensor provides us with data on the robot's orientation, acceleration, and angular velocity across three axes.

#### Picture

<div align="center">
<img src="images/imu.png" alt="IMU Sensor Picture">
</div>

#### Working Principle

An Inertial Measurement Unit (IMU) sensor combines accelerometers, gyroscopes and sometimes magnetometers to provide information about the robot's motion and orientation.

##### Accelerometer:
An accelerometer measures the acceleration forces acting on it, which can be due to gravity or movement.  
It consists of tiny mass-spring systems that deflect under acceleration, causing a change in capacitance or resistance that is measured and converted into an electrical signal.  
This signal is then used to calculate the acceleration in specific directions, helping determine linear movement and orientation relative to the ground.

<div align="center">
<img src="images/accl_working_principle.gif" alt="Accelerometer Working Principle">
</div>

##### Gyroscope:
A gyroscope measures the rate of rotation around an axis, providing information about the angular velocity.  
It often uses the Coriolis effect in vibrating structures, where the rotation causes a detectable shift in vibration patterns.  
This shift is measured and translated into rotational data, which can be integrated over time to track the orientation of the device.

<div align="center">
<img src="images/gyro_working_principle.png" alt="Gyroscope Working Principle">
</div>

##### Magnetometer:
A magnetometer measures the strength and direction of magnetic fields, including the Earth's magnetic field.  
It uses sensors like Hall-effect sensors or magnetoresistive sensors to detect magnetic flux changes.  
This data is used to determine the device's heading or orientation relative to the Earth's magnetic poles, often aiding in navigation and correcting drift in other sensors.

<div align="center">
<img src="images/magneto_working_principle.png" alt="Magnetometer Working Principle">
</div

Together, these measurements enable the IMU to determine the robot's orientation, movement, and position relative to its starting point.

#### Usage Example

Since an IMU provides information about the robot's orientation, acceleration, and angular velocity, we can use this data for various purposes, such as:

- Keeping track of the robot's movement and position in real-time, which is crucial for navigation.
- Stabilizing the robot to maintain a steady course or orientation, even on uneven surfaces.
- Assisting with complex maneuvers, such as turning accurately and maintaining balance during sharp movements.
- Perform precise movements, such as rotating to a specific angle or following a predefined trajectory.
- Integrate with other sensors to provide a comprehensive understanding of the robot's environment and actions.
- Detect and compensate for external disturbances, such as vibrations, shocks, or sudden changes in direction.

---

### Encoder

#### Description

Encoders are devices that convert mechanical motion into electrical signals.  
The Duckiebot DB21J is equipped with wheel encoders.  
These encoders provide data on the rotational position and speed of the robot's wheels, enabling precise measurement of distance traveled.

#### Picture

<div align="center">
<img src="images/encoder.jpg" alt="Encoder Picture">
</div>

#### Working Principle

Wheel encoders measure the rotation of a wheel or axle to provide information about position, speed, and direction.  
They convert rotational position into an electrical signal, which is then processed to extract the desired information.

##### Incremental and Absolute Encoders:

Incremental encoders generate a series of pulses corresponding to fixed rotation amounts, allowing for distance and speed calculations, but they require a reference point for absolute positioning. 

Absolute encoders, on the other hand, provide a unique position value for each rotational point, offering precise position data from the start without needing a reference.

<div align="center">
<img src="images/inc_vs_optical.png"  alt="Incremental vs Absolute Encoders">
</div>

##### Optical Encoders:

Optical encoders use an LED light source and a photodetector to read transparent and opaque segments on a rotating disc.  
The resulting light and dark patterns are converted into electrical signals, offering high precision and resolution.

<div align="center">
<img src="images/optical_enc.jpg" alt="Optical Encoder">
</div>

##### Magnetic Encoders:

Magnetic encoders utilize a magnetic disc and a sensor to detect changes in the magnetic field as the disc rotates.  
These changes are converted into electrical signals, making magnetic encoders robust and suitable for harsh environments, though they may offer slightly less precision compared to optical encoders.

<div align="center">
<img src="images/magnetic_enc.jpg" alt="Magnetic Encoder">
</div>

#### Usage Example

Encoders are essential for precise navigation and control of the Duckiebot.  
They provide the following benefits:

- Measuring the distance the robot has traveled by counting the number of wheel rotations.
- Calculating the speed of the robot, which is crucial for maintaining consistent and controlled motion.
- Enabling accurate control of the robot's movements, such as stopping at a specific point or maintaining a steady speed.

With the encoder data, we can improve the Duckiebot's capabilities in various ways:

- Implementing odometry to track the robot's position over time, which is vital for navigation and path planning.
- Ensuring precise movement and stopping distances, which is important for tasks like docking and obstacle avoidance.
- Integrating with other sensors to provide comprehensive data for more advanced control algorithms.

[Back to Index](README.md) | [Next: Actuators](actuators.md)

---

