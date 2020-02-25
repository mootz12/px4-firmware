# PX4 Drone Autopilot

[![Releases](https://img.shields.io/github/release/PX4/Firmware.svg)](https://github.com/PX4/Firmware/releases) [![DOI](https://zenodo.org/badge/22634/PX4/Firmware.svg)](https://zenodo.org/badge/latestdoi/22634/PX4/Firmware)

[![Build Status](http://ci.px4.io:8080/buildStatus/icon?job=PX4/Firmware/master)](http://ci.px4.io:8080/blue/organizations/jenkins/PX4%2FFirmware/activity)

[![Slack](https://px4-slack.herokuapp.com/badge.svg)](http://slack.px4.io)

This repository holds the [PX4](http://px4.io) flight control solution for drones, with the main applications located in the [src/modules](https://github.com/PX4/Firmware/tree/master/src/modules) directory. It also contains the PX4 Drone Middleware Platform, which provides drivers and middleware to run drones.

* Official Website: http://px4.io (License: BSD 3-clause, [LICENSE](https://github.com/PX4/Firmware/blob/master/LICENSE))
* [Supported airframes](https://docs.px4.io/en/airframes/airframe_reference.html) ([portfolio](http://px4.io/#airframes)):
  * [Multicopters](https://docs.px4.io/en/airframes/airframe_reference.html#copter)
  * [Fixed wing](https://docs.px4.io/en/airframes/airframe_reference.html#plane)
  * [VTOL](https://docs.px4.io/en/airframes/airframe_reference.html#vtol)
  * many more experimental types (Rovers, Blimps, Boats, Submarines, etc)
* Releases: [Downloads](https://github.com/PX4/Firmware/releases)


## PX4 Users

The [PX4 User Guide](https://docs.px4.io/en/) explains how to assemble [supported vehicles](https://docs.px4.io/en/airframes/airframe_reference.html) and fly drones with PX4.
See the [forum and chat](https://docs.px4.io/en/#support) if you need help!


## PX4 Developers

This [Developer Guide](https://dev.px4.io/) is for software developers who want to modify the flight stack and middleware (e.g. to add new flight modes), hardware integrators who want to support new flight controller boards and peripherals, and anyone who wants to get PX4 working on a new (unsupported) airframe/vehicle.

Developers should read the [Guide for Contributions](https://dev.px4.io/en/contribute/).
See the [forum and chat](https://dev.px4.io/en/#support) if you need help!


## Setup for PX4

#### Install Windows Cygwin

This gives you the toolchains needed to build / simulate PX4 firmware on Windows (and is also used to compile Pixhawk4 builds).

Download the MSI from [PX4](https://github.com/PX4/windows-toolchain/releases/tag/v0.8).
* Keep clicking next (would be good to leave installation in default locations)
* DO NOT CLICK THE BOX TO AUTO-CLONE REPO

#### Clone the Repo

NOTE: PX4 Documentation recommends using the Cygwin bash console when perfoming any terminal commands.

Navigate to the installation directory in your terminal of choice `C:\PX4\`

Launch the Cygwin bash console by running __run-console.bat__ with the command `.\run-console.bat`

Clone the repo: 
```
git clone https://github.com/mootz12/px4-firmware.git
```

When opening the project via VS Code, it will live at `C:\PX4\home\px4-firmware`

#### Test the Simulation

NOTE: You will need to have Java installed.

Navigate to your firmware from the Cygwin console with `cd px4-firmware`

Execute the command (this will take a long time the first time...):
```
make px4_sitl jmavsim
```

If you see the following error in your terminal output, follow the steps below:
```
WARNING: Could not open/create prefs root node Software\JavaSoft\Prefs at root 0x80000002. Windows RegCreateKeyEx(...) returned error code 5.
```
* Go into your Start Menu and type regedit into the search field (open the Registry Editor)
* Navigate to path HKEY_LOCAL_MACHINE\Software\JavaSoft
* Right click on the JavaSoft folder and click on New -> Key
* Name the new key `Prefs`
* CTRL+C to close the application in the terminal if you haven't already and try running jMAVSim again

Now that the jMAVSim is runnning, view the following [documentation](https://dev.px4.io/v1.9.0/en/simulation/jmavsim.html) to use it.

