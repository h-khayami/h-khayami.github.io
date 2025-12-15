---
layout: page
title: OLED Pixel Game with IMU Control
description: An interactive Arduino game with accelerometer-based controls and OLED display
img: assets/img/OLED_IMU.png
importance: 2
category: class projects
giscus_comments: false
---

## Project Overview

This is an interactive game developed for Arduino with an OLED display (128x64 pixels) where a player controls a pixel using an MPU9265 IMU (Inertial Measurement Unit) sensor to hit targets on the screen. The game demonstrates embedded systems programming, sensor integration, and real-time display rendering.

**Course**: CMSC 730 - Interactive Technologies in HCI  
**Term**: Fall 2023

## Video Demonstration

<div class="row mt-3 justify-content-center">
    <div class="col-12 col-md-10 col-lg-8 mt-3 mt-md-0">
        <div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
            <iframe src="https://www.youtube.com/embed/wP5WV88fNnM" 
                    frameborder="0" 
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
                    allowfullscreen
                    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
                    class="rounded z-depth-1">
            </iframe>
        </div>
    </div>
</div>
<div class="caption text-center">
    Watch the game in action - demonstrating IMU-based control and real-time gameplay on the OLED display.
</div>

## Key Features

- **IMU-Based Control**: Control the pixel using the MPU9265 accelerometer by tilting the device
- **Button Control**: Alternative control using physical buttons (UP, DOWN, LEFT, RIGHT)
- **Two Difficulty Levels**:
  - **Easy Mode** (Level 1): 4 active targets to hit
  - **Hard Mode** (Level 2): 2 active targets to hit
- **Real-time Rendering**: Smooth 25 FPS gameplay on SSD1306 OLED display
- **Collision Detection**: Accurate hit detection between pixel and targets
- **Game Timer**: Tracks completion time in seconds

## Hardware Components

### Electronics
- **Microcontroller**: ESP32 board
- **Display**: SSD1306 OLED Display (128x64 pixels, I2C)
- **IMU Sensor**: MPU9265 (9-axis motion tracking)
- **Buttons**: 7 push buttons for control and menu selection

### Pin Configuration

| Button | Pin | Function |
|--------|-----|----------|
| UP | 19 | Move pixel up |
| DOWN | 18 | Move pixel down |
| LEFT | 5 | Move pixel left / Select Easy mode |
| RIGHT | 17 | Move pixel right / Select Hard mode |
| MID | 16 | Middle button |
| SET | 4 | Settings button |
| RST | 0 | Reset button |

## Software Architecture

The project demonstrates clean object-oriented design with the following components:

### Core Classes

**`Pixel`** - Manages the player-controlled pixel
- Handles movement with boundary checking
- Position starts at center of screen (64, 32)

**`Targets`** - Manages up to 5 targets on screen
- States: ACTIVE, INACTIVE, HIT
- Random position generation within screen boundaries

**`Position`** - Simple 2D coordinate class
- Stores x, y coordinates
- Overloaded equality operators

**`Renderer`** - Static methods for display rendering
- Frame management
- Border, pixel, and target rendering
- Menu and game over screens

**`MPU9265 Driver`** - Custom IMU sensor driver
- Accelerometer and gyroscope reading
- I2C communication at address 0x68

## How to Play

1. **Setup**: Select difficulty level using LEFT (Easy) or RIGHT (Hard) button
2. **Control**: Tilt the device to move the pixel using the accelerometer, or use direction buttons for precise control
3. **Objective**: Navigate the pixel to hit all active targets
4. **Win**: Complete all targets as quickly as possible - your time will be displayed at the end!

## Technical Highlights

- **Real-time sensor fusion**: Integrated accelerometer data for smooth, responsive controls
- **Embedded systems programming**: Efficient memory usage and real-time rendering on resource-constrained hardware
- **Modular architecture**: Clean separation of concerns with dedicated classes for game logic, rendering, and sensor management
- **I2C communication**: Custom implementation of MPU9265 sensor driver
- **Frame rate optimization**: Maintained consistent 25 FPS gameplay

## Technologies Used

- **Arduino IDE** for development
- **C/C++** for embedded programming
- **I2C Protocol** for sensor and display communication
- **Adafruit GFX & SSD1306** libraries for graphics
- **MPU9265** accelerometer/gyroscope sensor

## Repository

The complete source code, including all class implementations and the custom MPU9265 driver, is available on GitHub:

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  <div class="repo p-2">
    <a href="https://github.com/h-khayami/pixel_game" target="_blank">
      <img src="https://github-readme-stats.vercel.app/api/pin/?username=h-khayami&repo=pixel_game&theme=default" alt="GitHub Repository">
    </a>
  </div>
</div>


---

*This project showcases the integration of multiple hardware components, real-time sensor processing, and interactive game design principles in an embedded systems context.*
