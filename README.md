# Autonomous Maze Solving Robot

An autonomous robot built with Arduino Uno that navigates and solves an unknown maze in real time using the **Left-Wall Following algorithm**, ultrasonic obstacle detection, and a PID-tuned motor control loop.

Built as a team mini-project (ECD334) at Government College of Engineering Kannur, under the guidance of Dr. Ajith K K.

## 🎯 Problem Statement
Design a low-cost, sensor-based robot capable of autonomously navigating an unknown maze without human intervention, demonstrating core principles of embedded systems, sensor integration, and real-time control.

## 🛠️ Tech Stack
- **Microcontroller:** Arduino Uno (ATmega328P)
- **Sensors:** 2x HC-SR04 Ultrasonic Sensors (front + left)
- **Motor Driver:** L298N (Dual H-Bridge)
- **Actuators:** DC Motors (left & right wheel)
- **Power:** 12V Li-ion battery (motors) + separate supply for Arduino
- **Language:** C/C++ (Arduino IDE)

## ⚙️ How It Works

The robot uses the **Left-Wall Following algorithm**:

1. Two ultrasonic sensors (front-facing and left-facing) continuously measure distance to the nearest wall/obstacle
2. **Decision logic:**
   - If no wall detected on the left → turn left
   - Else if a wall is too close ahead → turn right
   - Else → continue following the left wall, using **PID control** to maintain an ideal distance from it
3. A PID loop (Kp=3.3, Ki=0, Kd=5) continuously corrects left/right motor PWM values to minimize deviation from the ideal wall-following distance, smoothing out the robot's trajectory compared to a simple on/off (bang-bang) correction approach
4. The L298N motor driver receives PWM signals from the Arduino and drives the two DC motors accordingly

## 📐 System Architecture

Environment (Maze) → Ultrasonic Sensors → Arduino Uno (decision logic + PID) → L298N Motor Driver → Left DC Motor + Right DC Motor

## 📊 Results
- Successfully built and tested a working physical prototype
- Robot reliably follows the left wall and navigates turns within a physical maze model
- PID-based correction produced smoother wall-following behavior than a simple threshold-based
