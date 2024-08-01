---
layout: page
title: Laser diffraction
subtitle: project
---

# Laser Diffraction
**Group Number 1**

## Tutor Information
**Tutors:** Luca Porzio, Marcel Bajdel, Simone Vadilonga, Will Smith
**E-Mail:** luca.porzio@helmholtz-berlin.de, marcel.bajdel@helmholtz-berlin.de

## Project Description
This project uses a laser and a diffraction grating to perform diffraction experiments. The laser is controlled by a Raspberry Pi, which acts as a beam controller. The Raspberry Pi provides power and modulation signal to the laser in order to switch it on/off and control the beam intensity. The diffraction grating is mounted on a support which is fixed to the motor axis and oriented in a direction such that the laser is able to hit the grating surface. The motor and the grating are located inside the chamber to avoid interference with natural light.

To perform the experiments, the motor controller moves the motor stage changing the diffraction angle of the grating. The angle should be precisely calculated such that the diffraction pattern projected in the chamber will have a specific pattern. Finally, the camera is mounted to point at the projected diffraction pattern in the chamber to read and acquire data.

The whole setup is automated and controlled by EPICS IOCs. Phoebus is used to provide a graphical user interface to interact with the control system. Historical data are saved in the Archiver Appliance. In addition, a Bluesky instance is required to create experimental procedures and collect data.

### Required Components
#### Hardware components:
- 1 Laser (1mW - CAT 2).
- 1 Raspberry Pi model 3 or model 4.
- 1 Motor controller with 1 rotary stage motor (or 1 goniometer stage motor).
- 1 Diffraction grating mirror.
- 1 IP Camera.
- 1 cardboard chamber.

#### Software Components:
- EPICS IOC for Raspberry GPIO to control the laser.
- EPICS IOC for motor controller using ‘motor’ record.
- EPICS IOC for IP Camera using ‘areaDetector’.
- 1 or more Phoebus displays for SCADA system.
- Archiver Appliance.
- Alarm Server.
- Ophyd devices to interact with the IOCs in Bluesky.
- 1 or more Bluesky plans to execute experimental procedures.

## Project Objectives
- Demonstrate correct communication between hardware components.
- Implement EPICS IOC for the Raspberry GPIO with functions to control the Laser. Functions required are:
  - Switch on and off the Laser.
  - Set up PWM modulation (frequency and duty-cycle).
- Implement EPICS IOC for motor controller using the EPICS motor record. Demonstrate the following functionalities:
  - Homing Forward and Backwards.
  - Move Absolute.
  - Move Relative.
  - Setting up velocity.
- Implement EPICS IOC for the camera using EPICS areaDetector. Demonstrate the following functionalities:
  - Capture images with different rates.
  - Apply color conversion.
  - Apply background subtraction.
  - Computing statistics.
- Implement Phoebus GUI for Laser control, Motor control and Camera control.
- Demonstrate correct configuration of EPICS Alarm Server.
- Demonstrate correct configuration of EPICS Archiver Appliance.
- Implement Ophyd devices for laser, motor and camera.
- Demonstrate the correct functionalities of the Ophyd devices by running a Bluesky ‘scan’ plan using the motor and the camera.

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
