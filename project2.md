---
layout: page
title: Magnetic Field Measurement
subtitle: project
---

# Magnetic Field Measurement
**Groups Number 4  and 5**

## Tutor Information
**Tutors:** Maurizio Montis, Mauro Giacchini

**E-Mail:** maurizio.montis@lnl.infn.it, mauro.giacchini@lnl.infn.it

## Project Description
In this laboratory, students will develop and implement a control system to measure the magnetic field produced by a steerer, a critical component of a linear accelerator. Understanding and precisely controlling the magnetic field is essential for the optimal operation of the accelerator, as it directly impacts the trajectory and focus of the particle beam. These systems consist of electromagnets, called steerers, that generate magnetic fields to adjust the beam's path. By fine-tuning the magnetic field, the steerer ensures the beam remains on its intended course, thereby preventing collisions with the accelerator walls and ensuring that the particles reach their target with the desired energy and precision.

The laboratory setup for this exercise includes a steerer composed of four coils, a high current power supply remotely controlled via Ethernet, a teslameter for measuring the magnetic field also remotely controlled via Ethernet, and a stepper motor coupled with a motor driver. The motor driver is already equipped with an EPICS IOC, which facilitates integration and automation. The stepper motor is responsible for moving a magnetic field sensor through a dedicated kinematic transmission system, allowing precise spatial measurements of the magnetic field.

Students are tasked with creating a control system to automate the magnetic field measurements using the provided equipment. This involves programming the power supply to adjust the current through the steerer coils, interfacing with the teslameter to record magnetic field data, and coordinating the stepper motor to move the magnetic field sensor systematically. Through this exercise, students will gain practical experience in control systems, data acquisition, and the integration of various laboratory instruments, all essential skills in accelerator physics and engineering.

### Required Components 

#### Hardware components:
- 1x Steerer (2 coils – horizontal OR vertical)
- 1x High Current Power Supply 10V/20A 
- 1x Teslameter
- 1x Magnetic Field Sensor
- 1x Motor Driver
- 1x Stepper Motor
- 1x Kinematic transmission
- 1x Network switch
- 1x USB-to-RS232c converter

#### Software Components:
- VM and EPICS toolkit
- Phoebus application
- BlueSky and Ophyd applications
- Server with VxWorks OS and VSFTP service (for the motor driver)
  
## Project Objectives
- Demonstrate correct communication between hardware components
- Configure and test VME-based and EPICS IOC for motor drivers
- Verify the kinematic transmission with the stepper motor and the mechanical setup
- Implement EPICS IOC for the power supply and the teslameter
- Created the proper device support to interface the power supply and teslameter
  - teslameter:
    - zero-reset probe for initial measurements
    - read X, Y, Z, and the Average magnetic field from the probe
  - power supply:
    - enable power supply command and readback
    - current setpoint command
    - current and voltage readbacks
    - (optional) power supply fault status  
- Create Phoebus Control Panels devoted to supervising the entire setup
- Describe management and organization strategy
- Map the setup in a BlueSky service and define proper experimental operations



## Task Structure

| Responsible | Topic |
|-------------|-------|
| Student Name | Hardware setup |
| Student Name | EPICS layer |
| Student Name | Phoebus Screen and Archiver Appliance |
| Student Name | Ophyd + Bluesky |

## Tasks Description
### Hardware Setup

The experiment requires a dedicated LAN network to work properly: every device communicates via an ethernet port.

The principal characteristics of every element are indicated below:
* Power Supply
* Teslameter
* Motor Driver
* Network Switch
* Stepper Motor

#### **Power Supply**:
* electrical connections with steerer
* communication via an ethernet link
* serial and network communication setup via the web interface is required (require info authentication to the tutors)

#### **Teslameter**:
* connection to magnetic field sensor
* communication via an ethernet link
* network communication setup is required
  
#### **Motor Driver**:
* electrical connection with the stepper motor, DB25 to DB15 transition required
* network connection via ethernet link. Network configuration at OS level is required and done via serial communication (USB-to-RS232 converter required)

#### **Network Switch**:
* devices properly connected in the LAN

#### **Stepper Motor**:
* electrical connection with the motor driver, DB15 to DB25 transition required
* kinematic transmission is required to convert rotation movement in longitudinal movement
* limit switches are required to prevent dangerous positions for the sensor


### EPICS Layer

Every single device must be interfaced in EPICS, with the exception of the motor driver which already provides an IOC. 

There must be 2 IOCs, one for the power supply and one for the teslameter. Every IOC requires dedicated device support to proper interface the hardware in the EPICS environment.

The principal characteristics required for the control of every element are indicated below:

#### **Power Supply**:
* Device support with streamdevice
* List of commands available on the manual
* The power supply is controlled in current, proper EPICS records must be implemented for controls and readbacks
* (*optional*) Provide the set of information related to device diagnostics at the EPICS level

#### **Teslameter**:
* Device support with streamdevice
* List of commands available on the manual
* The teslameter provides the measurement of the magnetic field in 3 directions. Provided the proper set of EPICS records
  
#### **Motor Driver**:
* The IOC is already provided, analyze the list of PVs provided and identify the principal candidates for the control

#### **softIOC**:
* An additional IOC (softIOC) devoted to provide data and calculation required by the GUI (i.e. data for plots) can be implemented if considered suitable for the control system architecture


### Phoebus Screen and additional services

1. Phoebus screen to control the modulation of the laser pointer
2. Phoebus screen to control the motors (check the motor record repository for the standard UIs)
3. Phoebus screen to control the camera (check the Areadetector repositories)
4. Phoebus main screen as main entry point for the project
5. Setup the archiver appliance in Phoebus
6. (Optional) Define alarms (in the IOC database) and setup alarm-server and phoebus to display alarms


### Ophyd + Bluesky

Create an Ophyd device for the laser, motor record and areadetector camera.


## Final Presentation
Prepare a slideshow presentation with a duration of about 45 minutes. Each responsible defined in the Task Structure must present in details the work that the group has done. At the end of the presentation, the group must show a working demo of their project.
