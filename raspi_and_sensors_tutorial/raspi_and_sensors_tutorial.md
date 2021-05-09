# Interacting with Raspberry Pi and Sensors

This tutorial will walk through how to use your Raspberry Pi to interact with some common sensors used with ZotBins.

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

For this tutorial you can refer to this circuit here: https://www.circuito.io/app?components=9443,13959,200000,669681

![img](https://raw.githubusercontent.com/zotbins/Hardware_Hub/main/raspi_and_sensors_tutorial/imgs/full_circuit.png)

### GPIO Pins on a Raspberry Pi

![img](https://raw.githubusercontent.com/zotbins/Hardware_Hub/main/raspi_and_sensors_tutorial/imgs/gpio_key.jpg)

**Resources**
- [Raspberry DIY: How to Use the GPIO Pins on Your Raspberry Pi (with Safety Tips)](https://raspberrydiy.com/gpio-pins-tutorial-raspberry-pi/)
- [Circuit IO: How to Use Breadboards](https://www.circuito.io/blog/breadboards/)

### Making the Ultrasonic Circuit
We use a voltage divider using the 1 kohm resistor and a 2 kohm resistor (two 1 kohm resistor in series) because the Raspberry Pi can only handle certain voltages.

Let's connect Trig and Echo to the following:

    - Trig: GPIO 23
    - Echo: GPIO 24

![img](https://raw.githubusercontent.com/zotbins/Hardware_Hub/main/raspi_and_sensors_tutorial/imgs/ultrasonic_circuit.png)

**Resources**
- [The Pi Hut: HC-SR04 Ultrasonic Range Sensor on the Raspberry Pi](https://thepihut.com/blogs/raspberry-pi-tutorials/hc-sr04-ultrasonic-range-sensor-on-the-raspberry-pi)

### Making the Break-beam Circuit

We use a 10kohm pull-up resistor for the break-beam sensor.

![img](https://raw.githubusercontent.com/zotbins/Hardware_Hub/main/raspi_and_sensors_tutorial/imgs/breakbeam_circuit.png)

**Resources**
- [Circuit IO](https://www.circuito.io/app?components=9443,200000,669681)

### Running the Code
1. Run this Code for the Break-beam Sensor:

```python
import time
import datetime
import RPi.GPIO as GPIO
GPIO.setmode(GPIO.BCM)
GPIO.setup(4,GPIO.IN)
GPIO.setup(17,GPIO.IN)
GPIO.setup(27,GPIO.IN)



while True:
    sensor_state = GPIO.input(4)
    print(GPIO.input(4))
    if (sensor_state==0):
        while(sensor_state==0):
            sensor_state = GPIO.input(4)
            print(GPIO.input(4))
            print(datetime.datetime.fromtimestamp(time.time()).strftime('%Y-%m-%d %H:%M:%S'))
            time.sleep(1)
    time.sleep(1)
```

2. Run this code for the Ultrasonic Sensor:

```python
#Libraries
import RPi.GPIO as GPIO
import time

#GPIO Mode (BOARD / BCM)
GPIO.setmode(GPIO.BCM)

#set GPIO Pins
GPIO_TRIGGER = 23
GPIO_ECHO = 24

#set GPIO direction (IN / OUT)
GPIO.setup(GPIO_TRIGGER, GPIO.OUT)
GPIO.setup(GPIO_ECHO, GPIO.IN)

def distance():
    # set Trigger to HIGH
    GPIO.output(GPIO_TRIGGER, True)

    # set Trigger after 0.01ms to LOW
    time.sleep(0.00001)
    GPIO.output(GPIO_TRIGGER, False)

    StartTime = time.time()
    StopTime = time.time()

    # save StartTime
    while GPIO.input(GPIO_ECHO) == 0:
        StartTime = time.time()

    # save time of arrival
    while GPIO.input(GPIO_ECHO) == 1:
        StopTime = time.time()

    # time difference between start and arrival
    TimeElapsed = StopTime - StartTime
    # multiply with the sonic speed (34300 cm/s)
    # and divide by 2, because there and back
    distance = (TimeElapsed * 34300) / 2

    return distance

if __name__ == '__main__':
    try:
        while True:
            dist = distance()
            print ("Measured Distance = %.1f cm" % dist)
            time.sleep(1)

        # Reset by pressing CTRL + C
    except KeyboardInterrupt:
        print("Measurement stopped by User")
        GPIO.cleanup()
```

### Soldering Tips
1. Wear Safety Goggles just in case
    - if you melt the solder too fast, the solder might splatter and hit your eye
    - if you don't have goggles just be careful
2. Know that soldering irons are hot and don't touch it with your hand. Hopefully this is obvious.

    ![img](https://raw.githubusercontent.com/zotbins/Hardware_Hub/main/raspi_and_sensors_tutorial/imgs/soldering_meme.jpg)

3. Put a small blob of solder on your iron to help increase surface area of contact.
4. Make sure to touch both the copper pad and the pin/wire you are soldering.

![img](https://raw.githubusercontent.com/zotbins/Hardware_Hub/main/raspi_and_sensors_tutorial/imgs/soldering_tips.png)

![img](https://raw.githubusercontent.com/zotbins/Hardware_Hub/main/raspi_and_sensors_tutorial/imgs/good-bad-soldering.jpg)

### Practice soldering
1. Solder a stranded wire
2. Solder two wires together
3. Solder a pin to a PCB
4. Solder some male headers onto a PCB
5. Solder some female headers onto a PCB  
