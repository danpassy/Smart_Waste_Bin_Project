# BINOVATION: Smart Waste Bin Management System

## Project Overview
Welcome to the first version of our project titled BINOVATION. This project aims to develop an innovative waste management system that combines technology and ecology to optimize waste management.

## Objectives
The main goal of BINOVATION is to implement an intelligent waste bin system featuring three key functionalities:

### Real-Time Fill Level Measurement: 
The system is capable of continuously measuring the fill level of the bin to optimize collection cycles.

### Display of Fill Level: 
Information about the fill level is displayed in real-time on an integrated LCD screen on the bin, allowing for direct and easy visualization.

### Automatic Bin Locking: 
Once the bin reaches its maximum capacity, it automatically locks to prevent overflow and to signal that it is ready to be emptied.

### Dedicated Mobile Application
The data collected by the system is also accessible through a dedicated mobile application. This app allows users to view the fill levels of the bins in real-time, thus facilitating remote management and planning of collection interventions.

# TOF Distance Measurement And LCD Display  version 0.0.1

## Project Description - version 0.0.1
This first step of this project implements a real-time distance measurement system using the integrated Time-of-Flight (TOF) sensor on the STM32 B-U585I-IOT02A board. The system displays the fill level percentage on an I2C LCD screen and through serial communication. 

## Hardware Requirements
- STM32 B-U585I-IOT02A Development Board
- I2C LCD Display (16x2)
- USB Cable for power and communication

## Software Requirements
- STM32CubeIDE
- STM32CubeMX
- Terminal Software (e.g., Tera Term)

## Project Configuration in STM32CubeMX

### Clock Configuration
1. Set RCC to:
   - LSE: Crystal/Ceramic Resonator
   - HSE: Disabled
   - System Clock: 160 MHz

### Peripherals Configuration
1. **RTC Configuration:**
   - Clock Source: LSE
   - Hour Format: 24h
   - Asynchronous Prescaler: 127
   - Synchronous Prescaler: 255

2. **I2C1 Configuration:**
   - Mode: I2C
   - Speed Mode: Standard Mode
   - Clock Speed: 100 kHz

3. **GPIO Configuration:**
   - Configure pins for I2C1 (SCL/SDA)
   - Configure pins for TOF sensor

4. **Middleware** 
   - Configuration of TOF1


### Project Settings
1. Enable necessary peripherals:
   - I2C1/2
   - ICACHE
   - RTC
   - GPIO
   - RCC

2. Generate Code:
   - Generate peripheral initialization code
   - Include necessary HAL drivers

## Project Structure (IN TOF file)
- `app_tof.c/.h`: Main program entry point, TOF sensor initialization and processing
- `distance_measurement.c/.h`: Distance measurement and data processing
- `i2c_lcd.c/.h`: LCD display functions


## Features
- Real-time distance measurement (0-150cm)
- LCD display of bin fill level status
- Percentage calculation with inverse logic (0cm = 100%, 150cm = 0%)
- Measurement history with timestamps
- Serial output for debugging

## Usage
1. Configure the project in STM32CubeMX
2. Build and flash the program
3. Connect to serial port (115200 baud)
4. System will automatically:
   - Take measurements every 30 seconds
   - Display status on LCD
   - Log measurements to serial output

## Display Messages
- 0-33%: "Bin available" / "Bin level Low"
- 34-66%: "Bin available" / "Bin fill level MEDIUM"
- 67-95%: "Bin available" / "Bin fill level HIGH"
- 96-100%: "BIN UNAVAILABLE" / "BIN LOCKED"

## IMPORTANT


