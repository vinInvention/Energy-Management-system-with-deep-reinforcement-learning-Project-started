# Energy-Management-system-with-deep-reinforcement-learning-Project-started
Solar-Driven Intelligent Energy Management System Using Deep Reinforcement Learning

An off-grid, pure-DC solar system for a standard Nigerian 1-bedroom flat, designed for low-income and student apartments. A 100-120 W solar panel and a 3S Li-ion battery pack power low-power loads. An ESP32 controller schedules those loads under varying sunlight, first with hard-coded rules and then with a trained Deep Reinforcement Learning (DRL) agent.

Project goals
Size the load, battery, and solar panel from first principles, with every loss stage shown.
Build a rule-based ESP32 controller that serves as the performance baseline.
Train a DRL agent in simulation to manage load scheduling and battery use under variable weather.
Compare the DRL agent against the baseline on unmet demand and battery health.
Log peak load, average load, base load, and daily energy consumption.
System overview
Component	Specification
Solar panel	12V-class, 100-120 W
Battery	3S Li-ion, about 45 Ah (3S30P of 1.5 Ah cells, or 3S15P of 3 Ah cells), about 500 Wh
Charge control	CC/CV buck converter (XL4016) with Schottky diode and a BMS
Loads	2 LED bulbs (5V, via buck), 12V DC fan, 3 phone chargers (5V 2.4A), ESP32 electronics
Controller	ESP32 on a dedicated LM2596 buck converter, 5 NC relays
Sensing	Voltage divider and a current sensor (INA226)
Design load	about 287 Wh/day at the bus, about 69.8 W peak
Load classes
Critical: bulbs and phones
Non-critical: fan (shed first)
Always on: controller, sensors, relays
Project roadmap
Load sizing and energy budget
Battery sizing and pack configuration
Solar panel sizing
Embedded system requirements (ESP32 pin plan, sensors, relay map)
Simulation (PV, battery, load, and weather generator in MATLAB/Simulink)
Hard-coded controller (baseline)
DRL agent training to replace the hard-coded logic
Hardware deployment and multi-day field testing
Design approach
Loss accounting: each conversion stage (cable, diode, buck, BMS, battery round trip) is divided by its efficiency, and margins are multiplied.
Direct supply: in the daytime the panel feeds the loads directly, and only night energy passes through the battery.
Safety: a hardware BMS and fuses protect the battery independently of the ESP32 and the AI.
Tech stack

MATLAB and Simulink (Reinforcement Learning Toolbox), ESP32 (C/C++ firmware), Li-ion with a 3S BMS, NASA POWER solar data for Lagos.
