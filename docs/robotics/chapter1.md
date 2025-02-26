# 1. Sensors and Actuators

End effector is the tool at the end of the robot structure

## 1.1 Types of Actuators
* __Electric motors__ $\to$ the most common used actuators today
* _Hydraulics_ $\to$ first robots
* _Pneumatics_ $\to$ first robots
* Photo-reactive materials 
* Chemically reactive materials
* Thermally reactive materials
* Piezoelectic materials

### 1.1.1 DC Motors
Pros: 

* Cheap
* Small
* Easy to use
* Efficient

Cons:

* Brushes duration not high
* Brushes make noise
* Maximum speed is limited
* Cooling problems
* Pole number is limited

To overcome the problems, we can choose brushless DC (BLDC) motors, but BLDC motors are more expensive.

### 1.1.2 Stepper Motor
Pros:

* Rotation angle is proportional to input pulse
* No torque reduction when standstill
* High percision
* Bi-directional
* Realiable (Brushless)
* Openloop control applicable
* Speed operation range is large

Cons:

* Control circuit is required
* High current consumption
* Torque reduces at high speed
* May have resonances problem
* Hard to control for high speed (Require a high frequency inputs)

### 1.1.3 Servo Motors
Servo motor is a specific motor that can control the shaft to a specific position, commonly built from DC motors, it contains:

* Gear reduction
* Position sensor
* Control circuits

Most servo motor have the restriction of 180° travel range.

## 1.2 Types of Sensors
* Proprioceptive sensors $\to$ measure the internal state of the robot
* Extrocemptive sensors $\to$ measure the external state in the environments

### 1.2.1 Position Sensors
* Encoders
    * Incremental rotary enoders
    * Absolute rotary encoders

* Inertial sensor
    * Gyroscopes
    * Accelerometers
    * Magnetometers
    * IMU (Combination of above 3)

* TOF sensors
    * Ultrasonic sensors (sonar)
    * IR/LED sensors
    * camera (optic flow)
    * Lidar

* Tactile sensors
    * Binary
    * Analogical

* Proximity Perception