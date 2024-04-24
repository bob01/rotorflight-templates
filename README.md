[![GitHub license](https://img.shields.io/github/license/bob01/etxwidgets)](https://github.com/bob01/etxwidgets/main/LICENSE)


# Welcome to etx-Presets for RotorFlight
**Rapid setup for our ELRS RotorFlight electric and nitro R/C Helicopters, use at your own risk**


### About etx-Presets
Goal is to get a new flight controller configured as quickly possible allowing the user to get to familiar FBL setup with all of the boilerplate stuff out of the way.
The idea is...
- flash the FC with RotorFlight 2.0 or later
- from the RotorFlight configurator CLI load the preset files that match your hardware, model (e.g. 400 or 700 size), base profiles and rates (optional)
- get straight to the familiar - name the FBL, verify gyro orientation, servo center/travels/direction, mixer settings, tweak PIDs and governor
- verify that all controls are correct and setup is SAFE
- GO FLY

Even easier when used with transmitter models created with [etx-templates](https://github.com/bob01/etx-templates)


### Requirements / supported controllers
- RotorFlight 2 or later
- FlyDragon F722 v1 or v2 flight controller
- others will follow when available


### Features and some of the settings available with presets
- basic hardware settings for the chosen controller e.g. disable compass, barometer, set PID loop and black box frequency etc.
- ADC voltmeter config for BEC voltage (servo bus) telemetry if the ESC doesn't provide BEC telemetry
- halfduplex settings for ESCs with bi-directional telemetry for setup / programming
- basic RotorFlight settigs for modes, adjustments for a 4 bank setup (bank1, bank2, bank3, hold) battery/power settings, select ESC telemetry for battery voltage source etc, basic blackbox settings
- basic ELRS settings for RSSI channel (LQ) and ELRS telemetry sensor mappings compatible with models created with [etx-templates](https://github.com/bob01/etx-templates)
- default motor pole count to '10' (most common value for larger motors), enable governor feature etc if selected
- basic / conservative 400 or 700 filter settings including RPM filters and 4 dynamic notches
- basic servo settings for 1500us/333hz CCPM servos w/ geometry correction enabled (linear servo drives eg TDR2, TFF are rare) and a 760us/500hz or 1500us/333hz tail servo
- (optional) more locked in but still conservative 700 profile
- (optional) RACEFLIGHT rate which offers the more familiar rate / expo configuration


## Start by flashing your flight controller with an up-to-date version of RotorFlight if needed, if not skip to the next step...
![image](https://github.com/bob01/etx-presets-rotorflight/assets/4014433/48a03bde-bea6-47b2-8de5-ace766503f2f)


## calibrate the accellerometer and go to the CLI
![image](https://github.com/bob01/etx-presets-rotorflight/assets/4014433/0af0df2c-4f9f-470c-bc9c-f76dc089f127)
![image](https://github.com/bob01/etx-presets-rotorflight/assets/4014433/0d1e033d-d069-4d88-8f65-b9376efe48a9)


## first the hardware settings, there will be a dedicated folder for each hardware platform - be SURE to select the correct one and load the following files as shown
- e.g. if using an ESC with bidirectional telemetry connected to serial port 3 load the following presets
- - 0_base_fdf722_v2/0_base_adc_bus.txt (workaround for FDF722 v1/v2 lack of internal ADCs)
  - 0_base_fdf722_v2/0_base_serial_3_halfduplex.txt [EXT] (skip if NOT using an ESC with bidirectional telemetry connected to this port)
  - 0_base_fdf722_v2/0_base_serial_5_halfduplex.txt [GYRO] (skip if NOT using an ESC with bidirectional telemetry connected to this port)
  - 0_base_fdf722_v20_base.txt
![image](https://github.com/bob01/etx-presets-rotorflight/assets/4014433/2a297f50-037d-4f38-9239-14e9c165337a)


## next the general settings, follow the numbers...

- load the '0_' presets (load all, these are settings for a 4 back setup with standardized ELRS telemetry mappings)
- load the '1_'s
- - 1_motor_esc_gov_on.txt or 1_motor_esc_gov_off.txt
  - 1_motor_esc_halfduplex.txt (skip if NOT using an ESC with bidirectional telemetry)
- load the '2_filters_400/700' that best suits your model size
- load the '3_servos_' that's closest to your hardware
- (optional) load '4_profile_' for conservative but lively profile that we use as our starting point - headspeeds 1600, 1850, 2100rpm
- (optional) load '5_rates_race_med.txt' for a medium rate feel. We prefer the familiar Rate/Expo RACEFLIGHT parameters. ACTUAL rates were confusing to most. Note - if using RACEFLIGHT rates always leave the Acro+ parameter set to 0.
![image](https://github.com/bob01/etx-presets-rotorflight/assets/4014433/8e93d0f8-2a16-4cc3-b7f8-a7dd3c87537a)
![image](https://github.com/bob01/etx-presets-rotorflight/assets/4014433/afc8737a-1413-48ae-a0eb-4daa3916daa3)
![image](https://github.com/bob01/etx-presets-rotorflight/assets/4014433/2e7da4a3-c10e-46b4-b7eb-9dbc273b8e45)
### Done.


## From this point setup is more or less like any other FBL
- Configuration
- - set name and gyro sensor orientation/alignment
  - (optional) turn off the LED if it bothers you
  - (optional) the FDF722 v2's built in Rx is on serial port 1. We use serial port 3 [EXT] for telemetry, change to say port 5 if needed
- Power
- - set your battery capacity
- Motors
- - set ESC telemetry protocol
  - set main and tail gear ratios - accuracy here is vital for proper operation of gyro RMP filters
- Servos, mixer, profiles (same thing as bank/flight mode - focus on the PIDs) and rates should be familiar enough
- - don't forget to set governed headspeeds for each profile (bank)
- Verify that all controls are correct and setup is SAFE
- Done. Proceed with care as you would with any new system - have fun getting it dialed in.
![image](https://github.com/bob01/etx-presets-rotorflight/assets/4014433/6595cc5d-fa7b-4f54-9015-388bf9acf540)
![image](https://github.com/bob01/etx-presets-rotorflight/assets/4014433/09f1e78b-9702-4d8e-a157-3ddf82a3097b)
![image](https://github.com/bob01/etx-presets-rotorflight/assets/4014433/d53fa2f5-0c31-4ce0-8bec-c352fd0483c4)
![image](https://github.com/bob01/etx-presets-rotorflight/assets/4014433/72680d80-dc22-4aeb-bc4f-72bdb86c508a)


### Installation
- download etx-templates-main.zip from (from https://github.com/bob01/etx-presets-rotorflight) and unzip to a folder on your computer.
![image](https://github.com/bob01/etx-presets-rotorflight/assets/4014433/f25d3a92-deb3-4a5b-ad0a-57469f10c79a)


### Enjoy.
