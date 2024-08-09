---
layout: page
title: Magnetic Field Measurement
subtitle: project
---

# Laser Diffraction
**Group Number 1**

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
- Demonstrate correct communication between hardware components.
- Configure and test VME-based and EPICS IOC for motor drivers.
- Verify the kinematic transmission with the stepper motor and the mechanical setup
- Implement EPICS IOC for the power supply and the teslameter.
- Created the proper device support to interface the power supply and teslameter 
- Create Phoebus Control Panels devoted to supervising the entire setup.
- Describe management and organization strategy.
- Map the setup in a BlueSky service and define proper experimental operations

## Calculate the wavelength of the laser
When monochromatic light is incident on a grating surface, it is diffracted into discrete directions. We can picture each grating groove as being a very small, slit-shaped source of diffracted light. The light diffracted by each groove combines to form a set of diffracted wavefronts. This phenomenon is described by the grating equation:

$$\lambda = d \sin(\theta)$$

Where:
- m is the diffraction order
- λ is the wavelength of the light (in meters)
- d is the distance between the grooves of the grating
- θ is the angle between the central maximum and the maximum of order $m

### Aim of the Exercise
Calculate the grating density. To do this:
1. Mount your setup so that the laser is diffracting on the grating and hitting the black screen.
2. Make a ROI around the m=0 diffraction peak.
3. Scan the grating angle.

### Optional:
- GUI: Plot projections on the X,Y axes of the beam shape in the Phoebus camera display.
- Bluesky: Implement suspenders on Bluesky RunEngine monitoring laser beam PV to automatically suspend/resume a plan if the beam is lost.

## Task Structure

| Responsible | Topic |
|-------------|-------|
| Student Name | Hardware setup |
| Student Name | EPICS layer |
| Student Name | Phoebus Screen and Archiver Appliance |
| Student Name | Ophyd + Bluesky |

## Tasks Description
### Hardware Setup

Connecting all the devices to the network:

* camera (AXIS M1135 MK II)
* raspberry pi with laser (PICO 70142167 ARD-Punkt-LASER-MDI650)
* motor controller (MCS Smaract motor controller)

#### Camera

Camera is using power over ethernet, the switch that we provide can deliver it so there's no additional power supply needed. Once online the camera image is available in the network. 

#### Motor controller

Motor controller uses Ethernet interface to connect to the network and it exposes a set of ASCI instructions to debug it. Please check the controller user manual for the details. This device has to be set to the static IP address.

#### Raspberry PI
 
Raspberry PI uses Ethernet interface to connect to the network.

#### Laser pointer

The laser has to be connected to the Raspberry using GPIO pins for power and modulation. 

#### Gratings

You have a set of gratings to choose from for the experiment. They should be mounted to the motor using a physical support. 


### EPICS Layer

1. Create an IOC for the laser pointer that has to run on the Raspberry PI (you can find a template IOC in the Github)
  - the IOC must be able to control the modulation of the laser
2. Create the motor record based IOC for the MCS smaract controller (see github template)
  - each motor axis must be implemented using motor record
3. Create the areadetector IOC for the URL camera using the ADUrl module


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
