<div id="header" align="center">
  <img src="https://media.giphy.com/media/mFDWuDppjQJjite6FS/giphy.gif" width="300"/>
</div>

# Let's make a microcontroller!
Hello! In this tutorial, I will be teaching you how to construct a fully functioning ATmega328 from scratch.
There are two methods of this which is by constructing a circuit on breadboard or by soldering components on to a protoboard.
Either methods will generate same or similar result so choose whichever one you prefer.

## Pre-Prerequisites
Before you begin, you should have some knowledge of [how to use a breadboard](https://learn.sparkfun.com/tutorials/how-to-use-a-breadboard/all) or [soldering](https://www.youtube.com/watch?v=oqV2xU1fee8) and reading schematics.

## Prerequisites / Materials
You need these items in order to proceed with the construction and programming processes.
There will be Amazon links to obtain these materials.

- [ ] 1 x [Breadboard](https://a.co/d/gcQUHnz)
- [ ] 1 x [0.1 µF Ceramic Capacitor]()
- [ ] 1 x 10kΩ Resistor
- [ ] 1 x Push Button
- [ ] 23 x Header Pins
- [ ] 1 x ATmega328 or ATmega328P
- [ ] 1 x ATmega2560
- [ ] 1 x USB-A to USB-B Cable
- [ ] 1 x PC or Mac with following programs
  - [Arduino IDE](https://support.arduino.cc/hc/en-us/articles/360019833020-Download-and-install-Arduino-IDE)
  - Purdue Arduino MEGA Uploader <- Download the folder with the same name in this repository

If you are going the second route of *soldering* then get everything mentioned above **except** the breadboard and instead buy these...

- [ ] 1 x Protoboard
- [ ] 1 x [Soldering Kit](https://www.amazon.com/Soldering-Interchangeable-Adjustable-Temperature-Enthusiast/dp/B087767KNW/ref=sr_1_6?keywords=soldering%2Bkit&qid=1687306680&sr=8-6&th=1) *This has all you need!*

## Introduction
Phew, that was a long prerequisite :joy:. This will be an in-depth guide so *theoretically* you don't need to know all the things mentioned above in Pre-prerequisite but you should, it will be very handy.

So, why ATmega328? Well, I actually had to make this for a class and so I already know how to do everything and just wanted to pass down this knowledge. There is a full [article](https://www.electricaltechnology.org/2018/01/atmega-atmel-avr-microcontrollers.html) on what ATmega microcontrollers are capable of so you should read it ~~I didn't~~. It says on [ATmega328's Wikipedia](https://en.wikipedia.org/wiki/ATmega328) that "ATmega328 is commonly used in many projects and autonomous systems where a simple, low-powered, low-cost micro-controller is needed". But future BS aside, by being able to make and program a microcontroller, you will gain so much knowledge of how different components inside actually works. For example, you will be able to utilize its EEPROM or Electrically Erasable Programmable Read-Only Memory. EEPROM is often used to store configuration data for a microcontroller. This data could include things like the baud rate of the serial port, the IP address of the microcontroller, or the settings for a sensor. EEPROM is also sometimes used to store user data, such as a password or a list of contacts. See, you already learned something new about microcontrollers ~~hopefully~~.

Also before I go any further, read this [article](https://www.hnhcart.com/blogs/microcontrollers/a-1#:~:text=DIFFERENCE%20BETWEEN%20ATMEGA328%2F328P,could%20be%20a%2060nm%20process.) on the difference between ATmega328 and 328P. They are essentially the same thing with minor tweaks so the construction process will be the same except programming part. **BE AWARE OF WHAT KIND OF MICROCONTROLLER YOU HAVE**

Enough chit-chat, let's get down to business now.

## Step 1: The Setup
As you begin, notice how there is a half-circle on one side of the microcontroller and you see the small circle next to it? The pin adjacent to the circle is PIN 1. All pins that follow suit are in numerical order (so PIN 2, 3, and so on). 

![plot](/chip.jpg)

Grab the microcontroller chip and place it anywhere on the breadboard or protoboard. If you are building on a breadboard, push the microcontroller pins to the holes of the breadboard until you can't push any further. If you are building on a protoboard, push the pins through the holes then solder all of them. Be careful to not bend any pins.

Here is the schematic. Feel free to come back to this schematic whenever you're confused.

![plot](/schematic.jpg)

## Step 2: Power
Looking at the schematic, I have labeled PIN 7 and 8 as VCC and GND because that is the VCC and GND of ATmega328 microcontroller. 

![plot](/pinmap.png)

Connect these two pins via 0.1 µF Ceramic Capacitor then put two header pins after. Connect PIN 7 (VCC) to the power rail (+ Bus) and PIN 8 (GND) to the ground rail (- Bus).



