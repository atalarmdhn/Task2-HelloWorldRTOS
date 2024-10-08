# UART, ADC, and LED Task Example

This project demonstrates the use of UART communication, ADC (Analog-to-Digital Conversion), and LED control using FreeRTOS tasks on an STM32 microcontroller. The project involves the following features:
- UART communication for displaying ADC values and button status.
- ADC reading to obtain analog voltage values.
- LED control based on the ADC input value.
- Button detection for triggering actions.

## Table of Contents
- [Project Overview](#project-overview)
- [Hardware Setup](#hardware-setup)
- [Features](#features)
- [Tasks](#tasks)
- [How to Use](#how-to-use)
- [License](#license)

## Project Overview

This project is designed for an STM32 microcontroller using FreeRTOS for task management. It consists of multiple tasks that handle:
- Reading an ADC value (e.g., from a potentiometer).
- Displaying the ADC value over UART.
- Controlling LEDs based on the ADC value.
- Monitoring a button press to trigger events.

## Hardware Setup
![Gambar WhatsApp 2024-09-09 pukul 01 39 52_79be8b36](https://github.com/user-attachments/assets/23e77065-bf54-4fc0-a719-bfae5627d2b4)

- **Microcontroller**: STM32 (with STM32CubeIDE and HAL)
- **Peripherals**:
  - 1 Button
  - 5 LEDs
  - UART communication (e.g., USB-to-serial for PC communication)
  - Potentiometer for ADC input

### Pin Configuration
- **Button**: Connected to a GPIO pin, used to trigger LED display based on ADC value.
- **LEDs**: 5 LEDs connected to GPIO pins, their state is controlled by the ADC value.
- **UART**: USART2 used for UART communication (115200 baud rate).
- **ADC**: Channel 0 used for reading analog input from a potentiometer.

## Features

1. **ADC Reading**: Reads analog input from a potentiometer and converts it to a digital value (0–4095).
2. **LED Control**: Controls 5 LEDs based on the ADC value:
   - As the ADC value increases, more LEDs are turned on sequentially.
3. **UART Communication**:
   - Displays ADC value through UART.
   - User can press a button to display the ADC value on the serial monitor.
4. **Button Press Detection**: A button press triggers the ADC reading and LED control.

## Tasks

### 1. `pickButtonTask`
Monitors the state of a button. If the button is pressed, it updates a global flag (`button_pressed`).

### 2. `getADCTask`
Reads the ADC value from a potentiometer and stores it in the global variable `x_val`.

### 3. `dispLEDTask`
Controls the 5 LEDs based on the ADC value. LEDs are lit sequentially as the value increases.

### 4. `dispUARTTask`
Displays messages over UART, including ADC values and button press information. A simple menu is displayed for user interaction.

### 5. `StartDefaultTask`
Default task for handling background operations.

## How to Use

1. **Connect the hardware**: 
   - Connect 5 LEDs, 1 button, and a potentiometer as per the pin configuration.
   - Connect the UART to a PC for serial communication (USB-to-serial).
   
2. **Compile and Flash**: 
   - Use STM32CubeIDE to compile the code and flash it to the STM32 microcontroller.

3. **Run**: 
   - Open a serial terminal (e.g., PuTTY) with a baud rate of `115200`.
   - The terminal will display a menu.
   - Press the button to read the ADC value and observe the LEDs turning on based on the potentiometer position.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.
