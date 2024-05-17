---
layout: post
title: "Creating a Rubber Ducky USB Payload with Raspberry Pi Pico"
category: [howto]
tags: [cybersecurity,payload,raspberrypipico,duckyscript,rubberducky,security]
# pin: true
image:
  path: /assets/img/post9-payload/6547647856.jpeg
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
comments: true
---


In this tutorial, we'll guide you through turning your Raspberry Pi Pico into a Rubber Ducky using CircuitPython. This allows you to execute custom payloads on a target machine. Let's get started!

## Overview

The Raspberry Pi Pico, combined with CircuitPython, can be transformed into a Rubber Ducky - a USB device that automates keystrokes on a connected computer. We'll walk you through setting up your Raspberry Pi Pico, installing CircuitPython, and uploading a sample payload.

### What You'll Need

- Raspberry Pi Pico
- Micro-USB cable
- Computer with a USB port

## Step 1: Setting Up Your Raspberry Pi Pico

1. **Download CircuitPython for Raspberry Pi Pico**
   - Go to the [CircuitPython download page for Raspberry Pi Pico](https://circuitpython.org/board/raspberry_pi_pico/).
   - Download the `.uf2` file.

2. **Install CircuitPython on Your Raspberry Pi Pico**
   - Connect your Raspberry Pi Pico to your computer while holding the `BOOTSEL` button.
   - Release the button after connecting; your Pico should appear as a mass storage device named `RPI-RP2`.
   - Drag and drop the downloaded `.uf2` file onto the `RPI-RP2` drive. The drive will disconnect and reconnect as `CIRCUITPY`.

## Step 2: Setting Up the Environment

1. **Download Required Libraries**
   - Go to the [CircuitPython Libraries page](https://circuitpython.org/libraries) and download the latest version.
   - Extract the downloaded zip file.

2. **Copy Specific Libraries to Raspberry Pi Pico**
   - From the extracted `lib` folder, copy the following files to the `lib` folder on your `CIRCUITPY` drive:
     - `adafruit_hid`
     - `adafruit_wsgi`
     - `asyncio`
     - `adafruit_st7735r.mpy`
     - `adafruit_ticks.mpy`

3. **Download and Copy pico-ducky Files**
   - Visit the [pico-ducky GitHub repository](https://github.com/dbisu/pico-ducky).
   - Download the repository and copy its files to the root of your `CIRCUITPY` drive.

## Step 3: Creating the Payload

1. **Edit the Payload File**
   - Open the file named `payload.dd` on your `CIRCUITPY` drive.
   - Copy and paste the following Ducky Script into `payload.dd`:

```shell
REM Title: Hacker Glitch
REM Author: Faded (https://github.com/anonfaded)
REM Description: Simulates a glitchy screen hijack, displaying ominous messages and actions to evoke a sense of hacker intrusion. Shows ASCII art and in the end opens a browser to show a local image.
REM Target: Windows

ATTACKMODE HID STORAGE

DELAY 2000
GUI r
DELAY 1500
STRING powershell -Command "tree /F | Write-Host -ForegroundColor Green"
ENTER
DELAY 3000
ALT SPACE
REM close the powershell below
STRING c
DELAY 500

GUI r
DELAY 500
STRING cmd
ENTER
DELAY 1700
STRING Destroying
SPACE 
DELAY 500
STRING the system...
DELAY 500
STRING ...... 
DELAY 500
STRING ^_^

DELAY 1000
ALT SPACE
STRING c
DELAY 250
GUI r
DELAY 500
STRING notepad
DELAY 100
ENTER
DELAY 1000
CTRL t
STRING This computer is compromised. For details visit example.com.
ENTER

STRING <<<>>>
DELAY 1500

CTRL s
DELAY 800
STRING test.txt
ENTER
DELAY 550
ALT F4

GUI r
DELAY 800
STRING @$!#*&^%$#@!$^&*safsafs#*&^%$#@!$^&*afsaf234cfa67sac457fcas
ALT F4

DELAY 200
GUI r
DELAY 500
STRING notepad
ENTER
DELAY 500
CTRL t
DELAY 200

ALT
DELAY 250
STRING v 
DELAY 200 
STRING z
DELAY 200
STRING i
DELAY 200
ALT
STRING v 
DELAY 200 
STRING z
DELAY 200
STRING i
DELAY 200
ALT
STRING v 
DELAY 200 
STRING z
DELAY 200
STRING i
DELAY 200
ALT
STRING v 
DELAY 200 
STRING z
DELAY 200
STRING i
DELAY 200

ALT SPACE
DELAY 200
STRING x
DELAY 2000
STRING Faded was here...................
ENTER
DELAY 300

STRING                  _______                 
ENTER
STRING    _____    ____ \   _  \   ____ ___  ___
ENTER
STRING    \__  \  /    \/  /_\  \ /    \\  \/  /
ENTER
STRING     / __ \|   |  \  \_/   \   |  \>    < 
ENTER
STRING    (____  /___|  /\_____  /___|  /__/\_ \
ENTER
STRING         \/     \/       \/     \/      \/
ENTER

DELAY 1000

GUI r
DELAY 300
STRING firefox
ENTER

DELAY 2000
STRING file:///C:/Users/Username/Desktop/pic.jpg
DELAY 100
ENTER
```

## Description of the Payload

This payload, titled "Hacker Glitch," simulates a glitchy screen hijack to evoke a sense of hacker intrusion. It displays various ominous messages and actions, culminating in displaying ASCII art and opening a browser to show a local image.
 - You can rename the firefox to your preferred browser.
 - Download any pic from internet and save anywhere on your computer, after that do right click on that pic and open in brower by which you will get the link. Simply copy that URL and replace with the link in 3rd last line.

## Step 4: Running Your Payload

1. **Eject and Reconnect**
   - Safely eject your `CIRCUITPY` drive.
   - Reconnect the Raspberry Pi Pico to your computer.

2. **Test the Payload**
   - The payload will automatically execute when the Pico is connected.
   - Ensure you are testing in a safe and controlled environment.

## Additional Resources

- For more payload examples, visit my [GitHub repository](https://github.com/anonfaded/payloads).

## Conclusion

You've successfully turned your Raspberry Pi Pico into a Rubber Ducky! This tutorial covered the basics of setting up your device and running a sample payload. For more advanced payloads and further customization, explore the internet with `payload` keyword.

<br>
<br>
If you got any questions, you can ask in the comments below.

Happy hacking!
