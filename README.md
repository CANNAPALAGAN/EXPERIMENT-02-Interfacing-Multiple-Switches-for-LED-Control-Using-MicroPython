EXPERIMENT-02-Interfacing-Multiple-Switches-for-LED-Control-Using-MicroPython
NAME: DEVIKA D
DEPARTMENT: B.E CSE-CS
ROLL NO: 212224100010
DATE OF EXPERIMENT:
AIM
To interface multiple switches with the Raspberry Pi Pico and control LEDs using MicroPython.

APPARATUS REQUIRED
Raspberry Pi Pico

2 Push Button Switches

2 LEDs (Light Emitting Diodes)

330Ω Resistors

Breadboard

Jumper Wires

USB Cable

THEORY
FIGURE-01: RASPBERRY PI PICO PINOUT DIAGRAM

Raspberry Pi Pico is a microcontroller board based on the RP2040 chip. It supports MicroPython, making it suitable for IoT and embedded applications. The Raspberry Pi Pico is a compact microcontroller board featuring a 40-pin layout, including power, ground, GPIO, and communication interface pins. It operates with a dual-core ARM Cortex-M0+ processor and supports MicroPython and C/C++ programming.

The power pins include VBUS (5V from USB), VSYS (1.8V to 5.5V input), 3V3(OUT) (regulated 3.3V output), and multiple ground (GND) connections. The board offers 26 multi-purpose GPIO pins (GP0 to GP28), which can be used for digital input, output, PWM, and communication interfaces such as I2C, SPI, and UART. It also features three analog-to-digital converter (ADC) pins (GP26, GP27, GP28), used for reading analog sensor values, along with an ADC_VREF pin to set the reference voltage.

For communication, I2C (SDA, SCL), SPI (MOSI, MISO, SCK), and UART (TX, RX) interfaces are mapped across different GPIO pins, allowing seamless connectivity with sensors and peripherals. All GPIO pins support PWM (Pulse Width Modulation), making it useful for motor control, LED brightness adjustment, and sound applications. The BOOTSEL button enables USB mass storage mode for firmware flashing, while the DEBUG pins (SWD interface) provide debugging capabilities. With its low power consumption, flexible GPIO options, and rich interface support, the Raspberry Pi Pico is widely used for IoT, embedded systems, robotics, and automation projects.

WORKING PRINCIPLE

The switches are connected as inputs to GPIO pins of the Pico.

The LEDs are connected as outputs.

A MicroPython script reads the switch states and controls the LEDs accordingly.

CIRCUIT DIAGRAM
image Figure-01 circuit diagram of digital input interface

Connect switch 1 to GP2 and switch 2 to GP3.

Connect LED 1 to GP14 via a 330Ω resistor.

Connect LED 2 to GP17 via a 330Ω resistor.

Connect the other terminals of the switches to GND.

PROGRAM (MicroPython):
Interfacing Multiple switches with LED:
from machine import Pin
import time

led = Pin(0, Pin.OUT)

switch = Pin(1, Pin.IN, Pin.PULL_DOWN)

while True:
    if switch.value() == 1:   
        led.value(1)
        print("Switch ON → LED ON")
    else:                    
        led.value(0)
        print("Switch OFF → LED OFF")
    
    time.sleep(0.1)
OUTPUT:
![Uploading Screenshot (2).png…]()
![Uploading Screenshot (29).png…]()
Interfacing Multiple switches with Multiple LED's:
from machine import Pin
from time import sleep
print("Welcome Pi Pico")
switch1 = Pin(2, Pin.IN, Pin.PULL_UP)
switch2 = Pin(3, Pin.IN, Pin.PULL_UP)
led1 = Pin(15, Pin.OUT)
led2 = Pin(16, Pin.OUT)

while True:
    sw1_state = switch1.value()  
    sw2_state = switch2.value()
    
    print("Switch 1 state:", sw1_state)
    print("Switch 2 state:", sw2_state)
    
    
    led1.value(0)
    led2.value(0)
    
    if sw1_state == 1 and sw2_state == 1:
        led1.value(0)
        led2.value(0)
    elif sw1_state == 1:
        led1.value(0)
        sleep(0.5)
        led1.value(1)
    elif sw2_state == 1:
        led2.value(0)
        sleep(0.5)
        led2.value(1)
    
    sleep(0.1)
OUTPUT:
<img width="1920" height="878" alt="Screenshot (33)" src="https://github.com/user-attachments/assets/a8ea76c5-bb3e-4391-b01e-e68f3f7649df" />
<img width="1920" height="871" alt="Screenshot (35)" src="https://github.com/user-attachments/assets/aa5101d0-1fbf-4822-b2a5-78066a112406" />
<img width="1920" height="1200" alt="Screenshot (37)" src="https://github.com/user-attachments/assets/6082a1ef-0116-415b-a646-9a90b5c84b11" />
<img width="1920" height="859" alt="Screenshot (36)" src="https://github.com/user-attachments/assets/9ab361f4-e1be-41ef-a1b5-61cf73e78a2f" />

RESULTS
The multiple switches connected to the Raspberry Pi Pico successfully controlled the LEDs based on their states, confirming the proper interfacing of digital inputs and outputs.

About
Interfacing-Multiple-Switches-for-LED-Control-Using-MicroPython

Resources
 Readme
 Activity
Stars
 0 stars
Watchers
 0 watching
Forks
 0 forks
Report repository
Releases
No releases published
Packages
No packages published
Footer
