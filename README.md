<div id="header" align="center">
  <img src="https://media.giphy.com/media/mFDWuDppjQJjite6FS/giphy.gif" width="500"/>
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
- [ ] 1 x 10 kΩ Resistor
- [ ] 1 x Push Button
- [ ] 23 x Header Pins
- [ ] 1 x ATmega328
- [ ] 1 x ATmega2560
- [ ] 1 x USB-A to USB-B Cable
- [ ] 1 x PC or Mac with following programs
  - bootload_flash <- Download the .zip file with the same name in this repository then unzip it.
  - Command Prompt or Terminal

If you are going the second route of *soldering* then get everything mentioned above **except** the breadboard and instead buy these...

- [ ] 1 x Protoboard
- [ ] 1 x [Soldering Kit](https://www.amazon.com/Soldering-Interchangeable-Adjustable-Temperature-Enthusiast/dp/B087767KNW/ref=sr_1_6?keywords=soldering%2Bkit&qid=1687306680&sr=8-6&th=1) *This has all you need!*

Once you have every box checked, you may proceed to the next steps.

## Introduction
Phew, that was a long prerequisite :joy:. This will be an in-depth guide so *theoretically* you don't need to know all the things mentioned above in Pre-prerequisite but you should, it will be very handy.

So, why ATmega328? Well, I actually had to make this for a class and so I already know how to do everything and just wanted to pass down this knowledge. There is a full [article](https://www.electricaltechnology.org/2018/01/atmega-atmel-avr-microcontrollers.html) on what ATmega microcontrollers are capable of so you should read it ~~I didn't~~. It says on [ATmega328's Wikipedia](https://en.wikipedia.org/wiki/ATmega328) that "ATmega328 is commonly used in many projects and autonomous systems where a simple, low-powered, low-cost micro-controller is needed". But future BS aside, by being able to make and program a microcontroller, you will gain so much knowledge of how different components inside actually works. For example, you will be able to utilize its EEPROM or Electrically Erasable Programmable Read-Only Memory. EEPROM is often used to store configuration data for a microcontroller. This data could include things like the baud rate of the serial port, the IP address of the microcontroller, or the settings for a sensor. EEPROM is also sometimes used to store user data, such as a password or a list of contacts. See, you already learned something new about microcontrollers ~~hopefully~~.

Enough chit-chat, let's get down to business now.

## Step 1: The Setup
As you begin, notice how there is a half-circle on one side of the microcontroller and you see the small circle next to it? The pin adjacent to the circle is PIN 1. All pins that follow suit are in numerical order (so PIN 2, 3, and so on). 

<div align="center">
  
  ![plot](/chip.jpg)

</div>

Grab the microcontroller chip and place it anywhere on the breadboard or protoboard. If you are building on a breadboard, push the microcontroller pins to the holes of the breadboard until you can't push any further. If you are building on a protoboard, push the pins through the holes then solder all of them. Be careful to not bend any pins.

Here is the schematic (drawn by my friend Sam) and pin diagram of ATmeag328. Feel free to come back to these whenever you're stuck or confused.

![plot](/schematic.jpg)
![plot](/pinmap.png)

## Step 2: Power
Connect PIN 7 and 8 with 0.1 µF Ceramic Capacitor then put two header pins after. Connect the header pins of PIN 7 (VCC) to the power rail (+ Bus) and PIN 8 (GND) to the ground rail (- Bus).

This is how you will be able to power on the microcontroller.

"VCC stands for **Voltage Common Collector** and is the supply voltage for the circuit. It is usually connected to the positive (+) terminal of the power supply and is used to provide power to the various components of the circuit. GND on the other hand is **Ground** and is a reference point for the circuit and is commonly used as a return path for current. It is usually connected to the negative (-) terminal of the power supply, and is considered to be at zero voltage potential."

## Step 3: Reset Switch
As stated in the schematic, your PIN 1 (PC6) will be the reset switch. The ATmega can work without a reset button. Powering down the controller will reset it. In-circuit programmer will also reset the controller every time new firmware is loaded. But by having a dedicated reset switch, it is really easy to reset the microcontroller by push of a button. There are many reasons and here's top reasons why.

1. The reset switch allows you to manually initiate a system reset, which is crucial during the initialization phase of a microcontroller-based circuit. When the reset button is pressed, the microcontroller starts executing the program from the beginning, ensuring a known and consistent state for your system.

2. During the development and debugging process, a reset switch is particularly useful. It provides a quick and convenient way to reset the microcontroller and restart your program, allowing you to test different code sections or troubleshoot any issues you may encounter.

3. In certain scenarios, your program may encounter errors or unexpected behavior that cause the microcontroller to become unresponsive or stuck. By incorporating a reset switch, you can easily reset the microcontroller to resolve such issues without the need for power cycling the entire circuit.

Connect 10 kΩ Resistor to the power rail and ground rail. Place push button on the board connecting one leg to the ground rail and the other leg to the resistor.

Now you have a reset switch.

## Step 4: PORTs
You are almost done now. Practically, you're already done but we will be putting header pins to the pins of the microcontroller to easily connect and disconnect cables to use different ports of the microcontroller. Microcontrollers typically have various types of ports that serve different purposes. 

Here are some common types of ports found in microcontrollers:

1. General-Purpose Input/Output (GPIO) Ports: These ports allow the microcontroller to interface with external devices by providing digital input or output. Each GPIO pin can be individually configured as an input or output pin, allowing the microcontroller to read sensor data or control actuators.

2. Analog Input Ports: These ports are used to read analog signals from sensors or other analog devices. They usually have analog-to-digital converters (ADCs) that convert the analog voltage or current into a digital value that can be processed by the microcontroller.

3. Serial Ports: Microcontrollers often have one or more serial ports, such as UART (Universal Asynchronous Receiver/Transmitter), SPI (Serial Peripheral Interface), or I2C (Inter-Integrated Circuit). These ports enable the microcontroller to communicate with other devices using serial communication protocols.

4. Pulse Width Modulation (PWM) Ports: PWM ports generate digital signals with varying duty cycles. They are commonly used for controlling the speed of motors, brightness of LEDs, or generating analog-like signals.

5. Interrupt Ports: Interrupt ports allow the microcontroller to respond to external events or signals in a timely manner. When an interrupt is triggered, the microcontroller interrupts its current task and executes an interrupt service routine (ISR) to handle the event.

You can see which pins correspond to different types of ports on the schematic above. Now, place header pins anywhere on the breadboard/protoboard and connect the pins via wires. Now you are done with the construction and all there is left is programming the board to give it life!

As an example, here is my final product. Sorry it's a bit messy.

<p align="center">
  <img src="https://github.com/kyuhwan720/Making-ATmega328/blob/e368e088b65e29550cb897805fad50d6fbf02aca/finalproduct.png" height="750">
</p>


## Step 4-1: Quick Q&A
No, don't worry you are done with the construction process. I just wanted to have this moment to look back at some concerns you might've had during it. 

One question that many would ask is why I didn't include a crystal oscillator. Well, I was lazy. I know that ATmega328 has an internal oscillator that runs at a frequency of 8 MHz so I simply skipped this step of including an external one. If you require a more precise and stable clock signal, especially for applications that involve timekeeping or communication protocols, you should use an external crystal oscillator. 

But this tutorial isn't to make a standalone microcontroller. As stated above, we will be needing an ATmeag2560 to use it as an In-system programmer (ISP). To use this ATmega328, you will need ATmega2560 to bootload and program the controller. So we are using the Atmega328 in an Arduino board, the Arduino Uno, for example, comes with a 16 MHz crystal oscillator by default. This allows you to take advantage of the more accurate timing capabilities of the external crystal oscillator. To learn more about ISP, here is the [Wikipedia](https://en.wikipedia.org/wiki/In-system_programming) page.

For you Tl;dr people, you don't need a crystal oscillator at least for this tutorial. But you can add it if you eventually want to make a standalone microcontroller that has faster clock speed without using another Arduino board.

Another question is why I didn't use Arduino IDE. There are other tutorials online that advocates Arduino IDE by opening ArduinoISP to bootload the ATmega328. I personally don't like this method because one big reason: It didn't work for me. The aforementioned tutorials are all based on the older versions of Arduino IDE so there are some changes in the new versions available today. The ArduinoISP stayed the same but for some reason, the way this IDE interacts with the board changed and it does not work. My friends can all attest that bootloading through Arduino IDE did not work for them. If you had luck and got it to work, then good for you! But I personally don't like this method and will teach you how to flash the microcontroller using command prompt or terminal. 

Also before I go any further, read this [article](https://www.hnhcart.com/blogs/microcontrollers/a-1#:~:text=DIFFERENCE%20BETWEEN%20ATMEGA328%2F328P,could%20be%20a%2060nm%20process.) on the difference between ATmega328 and 328P. They are essentially the same thing with minor tweaks so the construction process will be the same except programming part. **BE AWARE OF WHAT KIND OF MICROCONTROLLER YOU HAVE.**

If you have more questions, send me a DM on Discord!

<div align="center">
  
  [![Discord Presence](https://lanyard.cnrad.dev/api/268325031342243843)](https://discord.com/users/268325031342243843)

</div>

## Step 5: Programming (Bootload)
So you have a fully finished board on the outside but there's nothing inside, yet. Now is the time to grab your ATmega2560 and connect it to your PC or Mac's USB port. You now need to make some connections between ATmega2560 and ATmega328. Follow the following table to do so. Refer back to the schematic to see where the PINs are located.

<div align="center">

  | ATmega2560   | ATmega328     |
  | ------------ |:-------------:|
  |5V            | VCC (PIN 7)   |
  |GND           | GND (PIN 8)   |
  |Digital PIN 50| MISO (PIN 18) |
  |Digital PIN 51| MOSI (PIN 17) |
  |Digital PIN 52| SCK (PIN 19)  |
  |Digital PIN 53| RESET (PIN 1) |

</div>

<p align="center">
  <img src="https://github.com/kyuhwan720/Making-ATmega328/blob/e368e088b65e29550cb897805fad50d6fbf02aca/bootload.png" height="650">
</p>
<p align="center">
  It should look something like this.
</p>

<div id="header" align="center">
  <img src="https://im4.ezgif.com/tmp/ezgif-4-156a8e9837.gif"/>
</div>

Now that you have everything connected properly, it's time to flash! No, please keep your pants on sir. Flashing means to write a new program to the microcontroller's flash memory. This can be done using the avrdude command-line tool. Unzip the bootload_flash.zip file. Once you did that, follow the GIF to open the command prompt that only pertains to this folder so you don't have to type C:\Users\username\folder\bootload_flash\... in the command prompt all the time to do anything.

Before we continue, we need to figure out which COM port our ATmega2560 is connected to. To check, simply open device manager and check COM port section. In this example, we can see that the ATmega is connected to COM3.

![com](https://github.com/kyuhwan720/Making-ATmega328/assets/133463914/855b8ed2-c8ae-467e-813a-d6e7c5a18efc)

Finally, go to the command prompt that is opened up. Type the following code and *voilà* your microcontroller is fully finished!

```
avrdude -c arduino -P com3 -p ATMEGA328 -b 19200 -U flash:r:sdint.hex:r
```

A little side note: If you are using ATmega328P for this build, just change the code to 

```
avrdude -c arduino -P com3 -p ATMEGA328P -b 19200 -U flash:r:sdint.hex:r
```

## Step 5: Programming (Flashing programs)
The bootload_flash folder contains .c file and .hex files for convenience. test.hex file is to test the IO PORTs. PORTC is input and PORTD is output. blinky.hex is to test PWM. For this, ADC0 is input and OC1A is output. You can simply upload the hex files on to the microcontroller by 

```
avrdude -c arduino -P com3 -p ATMEGA328P -b 19200 -U flash:w:[filename].hex:i
```

You can always change or create a new .c file in your preferred IDE then extract .hex file from it to program your board however you like it. Just make sure to include these two lines at the top of .c file.

```
#include <avr/io.h> // This contains the definitions of the terms used
#include <util/delay.h> // This contains the definition of delay function
```

