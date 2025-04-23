# Fridgin Awesome

A fermentation chamber controller for beer brewing implemented using ESPHome. This project aims to replicate the sophisticated temperature control logic from the BrewPi project, with native Home Assistant integration. By using the ESPHome framework, the source code aims to be vastly more accessable to the novice DIYer and can be easily modified to suit your specific needs.

### Inspiration

This project is heavily inspired by and based on the control algorithms from the original [BrewPi](https://github.com/BrewPi) project. A shoutout also to [BrewPiLess](https://github.com/vitotai/BrewPiLess) which provides an ESP8266 / ESP32 based implementation without the Raspberry Pi.

### Features

- Sophisticated temperature control logic using a state machine
- Adaptive overshoot prediction for minimal temperature fluctuations
- PID controller for beer temperature management
- Different control modes:
  - **Beer Mode**: Regulates beer temperature (using PID to control fridge temperature)
  - **Fridge Mode**: Directly regulates fridge/chamber temperature
  - **Profile Mode**: For future recipe-based temperature profiles (not yet implemented)
- Peak detection algorithms to learn the thermal characteristics of your fermentation chamber

This project is designed to integrate with Home Assistant. There is no built in web interface on the device.

## Current Status

This project is a work in progress. The core temperature control logic is implemented and functional, but some features like temperature profiles are still under development.

## Hardware Requirements

- ESP32 development board
- Two DS18B20 temperature sensors:
  - One for beer temperature
  - One for fridge/chamber temperature
- Relay-controlled heating element
- Relay-controlled cooling element (refrigerator/freezer)
- 20x4 I2C LCD character display (optional)
- Rotary encoder with pushbutton for interface (optional)

Note: This project is designed to be pin compatible with the [BrewPiLess](https://github.com/vitotai/BrewPiLess) project by default.

## Installation
When installing via the [ESPHome addon](https://esphome.io/guides/getting_started_hassio.html) in Home Assistant, simply add your new device via the dashboardand then add the following to your yaml configuration and run the install.
```
packages:
  remote_package: 
    url: https://github.com/sryburn/fridgin-awesome/
    file: fridgin-a.yaml

substitutions:
  # Update these with your actual addresses
  fridge_temp_address: '0x31031687b04aff28'
  beer_temp_address: '0xd103168221c1ff28'    
```
Your 1-wire addresses can be obtained from the device logs after the installation and updated accordingly. Note that all definitions contained in system_config.yaml (and elsewhere) can be overidden in your device yaml file, see https://esphome.io/components/packages.html. 

When installing via the [ESPHome CLI](https://esphome.io/guides/installing_esphome.html), simply clone the repo, edit device_config.yaml as required, add your secrets .yaml file and/or edit base_config.yaml as required.
run `esphome run fridgin-a.yaml` (as per https://esphome.io/guides/cli.html#run-command) to compile and upload to your device.

