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
|Pros | Cons |
|-----|------|
| Cheap | Brushes duration not high |
| Small | Brushes make noise |
| Easy to use | Maximum speed is limited |
| Efficient | Cooling problems|
| | Pole number is limited | 

To overcome the problems, we can choose brushless DC (BLDC) motors, but BLDC motors are more expensive.

### 1.1.2 Stepper Motor
|Pros | Cons |
|-----|------|
| Rotation angle is proportional to input pulse | Control circuit is required |
| No torque reduction when standstill | High current consumption |
| High percision | Torque reduces at high speed |
| Bi-directional | May have resonances problem |
| Realiable (Brushless) | Pole number is limited | 
| Openloop control applicable | Hard to control for high speed (Require a high frequency inputs) |
| Speed operation range is large | |

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
* Position Sensors
    * GPS
        * Not work indoor, underwater, in urban canyon
    * Encoders
        * Incremental rotary enoders

            2 sensors with the phase shifted by 90°, and the resolution then becomes $360°/4N$, $N$ is the number of the steps, and also for this installment, we can find the rotating directions:

            CCW for `11` followed by `10`

            CW for `11` followed by `01`

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