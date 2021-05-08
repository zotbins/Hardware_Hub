# Interacting with Raspberry Pi and Sensors

This tutorial will walk through how to use your Raspberry Pi to interact with some common sensors used with ZotBins.

### Table of Contents
1. Materials and Pre-requisites
1. Getting Familiar with the Terminal

### Materials and Pre-requisites
To follow along this tutorial you will need:
- a Raspberry Pi 3 with the latest Raspbbery Pi OS
    - follow these instructions here: https://www.raspberrypi.org/software/
- T-Cobbler GPIO Breakout w/ Ribbon Cable
- Break-beam Sensor
- Ultrasonic Sensor (HC-SR04)
- 1, 10 kohm Resistor
- 3, 1 kohm Resistor  
- Breadboard
- Prototyping Boards
- Solid Core Wire
- Soldering Iron
- Solder
- Helping Hands (recommended for Soldering)

### Circuit Overview

This is what the circuit looks like for a typical ZotBins setup at UCI. In the image below we can see the breakbeam sensors, the ultrasonic sensor, and the loadcells all connected to the Raspberry Pi using the GPIO pins. We'll only be working on the Ultrasonic circuit and the Breakbeam Circuit in this tutorial.

![img](https://raw.githubusercontent.com/zotbins/Hardware_Hub/main/raspi_and_sensors_tutorial/imgs/full_circuit.png)

### GPIO Pins on a Raspberry Pi

![img](https://raw.githubusercontent.com/zotbins/Hardware_Hub/main/raspi_and_sensors_tutorial/imgs/gpio_key.jpg)

**Resources**
- [Raspberry DIY: How to Use the GPIO Pins on Your Raspberry Pi (with Safety Tips)](https://raspberrydiy.com/gpio-pins-tutorial-raspberry-pi/)
- [Circuit IO: How to Use Breadboards](https://www.circuito.io/blog/breadboards/)

### Making the Ultrasonic Circuit
We use a voltage divider using the 1 kohm resistor and a 2 kohm resistor (two 1 kohm resistor in series) because the Raspberry Pi can only handle certain voltages.

![img](https://raw.githubusercontent.com/zotbins/Hardware_Hub/main/raspi_and_sensors_tutorial/imgs/ultrasonic_circuit.png)

**Resources**
- [The Pi Hut: HC-SR04 Ultrasonic Range Sensor on the Raspberry Pi](https://thepihut.com/blogs/raspberry-pi-tutorials/hc-sr04-ultrasonic-range-sensor-on-the-raspberry-pi)

### Making the Break-beam Circuit

We use a 10kohm pull-up resistor for the break-beam sensor.

![img](https://raw.githubusercontent.com/zotbins/Hardware_Hub/main/raspi_and_sensors_tutorial/imgs/breakbeam_circuit.png)

**Resources**
- [Circuit IO](https://www.circuito.io/app?components=9443,200000,669681)

### Getting Familliar with the Terminal

In this step we will use the terminal to interact with running some example code. If you hate the terminal, you can follow these steps by using a Python IDE such as Geany or Thonny Python IDE that should come with the default Raspberry Pi OS.

1. open the terminal with the shortcut: `ctrl + alt + t`
2. clone the repo

### Running the Code
1
### Soldering Tips
1. Wear Safety Goggles just in case
    - if you melt the solder too fast, the solder might splatter and hit your eye
    - if you don't have goggles just be careful
2. Know that soldering irons are hot and don't touch it with your hand. Hopefully this is obvious.

    ![img](https://raw.githubusercontent.com/zotbins/Hardware_Hub/main/raspi_and_sensors_tutorial/imgs/soldering_meme.jpg)

3. Put a small blob of solder on your iron to help increase surface area of contact.
4. Make sure to touch both the copper pad and the pin/wire you are soldering.

###
