---
layout: page
title: Laser diffraction
subtitle: project
---

# Laser Diffraction
**Group Number 1**

## Tutor Information
**Tutor:** Luca Porzio  
**E-Mail:** luca.porzio@helmholtz-berlin.de

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

\\(m \lambda = d \sin(\theta)\\)

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
Detailed description of all the pieces of hardware, interfaces and protocols, required setup. (e.g. controller SA-500 has 4 channels, connector are type D-Sub 15, Serial interface RS-232. A Serial-to-Ethernet device is needed,...)

### EPICS Layer
Detailed description of EPICS components to use, requirements for the IOCs and mandatory functions to implement. (e.g. We need 4 IOCs, motor IOCs must use motor record. Power Supply must use StreamDevice, protocol description is inside this manual,...)

### Phoebus Screen and additional services
Requirements for the screens, functionalities to implement. (e.g. The OPI must show information about controller, serial number, firmware version, …, one button must trigger acquisition of the camera,… , change color of the LED based on threshold,…, setup archiver for these PVs)

### Ophyd + Bluesky
Detailed description of plans to implement, functions and other information about the experiments. (e.g. create a scan plan that moves a motor by 20 degrees 50 times, implement callback to plot data against timestamp, create ophyd device with the function to calibrate the motor,...)

## Final Presentation
Prepare a slideshow presentation with a duration of about 45 minutes. Each responsible defined in the Task Structure must present in details the work that the group has done. At the end of the presentation, the group must show a working demo of their project.
