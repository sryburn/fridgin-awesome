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

This project is designed to be pin compatible with the BrewPiLess project.

## Integration with Home Assistant

This project is designed to integrate with Home Assistant. There is no built in web interface on the device.

## Installation

Compile fridgin-a.yaml and upload to your ESP32 device using the ESPHome CLI or ESPHome add-on for Home Assistant. All system parameters, pin definitions etc are contained in the system_config.yaml file. You should also have a secrets.yaml file present or otherwise edit base_config.yaml directly with your wifi credentials, API key etc.

