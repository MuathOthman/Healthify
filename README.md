# Healthify

## Developed by

- [@isakovero](https://www.github.com/isakovero)
- [@MuathOthman](https://www.github.com/MuathOthman)
- [@Agrinsadon](https://www.github.com/Agrinsadon)
- [@muhissadik](https://www.github.com/muhissadik)

## Project Demo


## 1 Introduction

This report presents the development process of a heart rate detection and
analysis system for the first-year IT engineering students' Hardware 2 course at
Metropolia University of Applied Sciences. The project aims to create a userfriendly device that accurately measures heart rate and heart rate variability
(HRV) using photoplethysmography (PPG) technology.

The topic of the project is the development of a heart rate detection and analysis
system that integrates PPG technology, stores server data, and connects to the
Kubios Cloud HRV analysis service. The project's goal is to make a user-friendly
tool to help people track their heart rate and HRV, so they can understand their
stress and recovery better.

The motivation behind this project is to provide a practical learning experience
for the first-year IT engineering students, allowing them to apply their knowledge
and skills from various courses, such as Health Technology, Digital Circuits, Linux,
and Networks. In addition, the project aims to improve students' understanding
of the relationship between heart rate and resilience, thereby improving their
overall health.

The main goals of the project are to create a heart rate system with PPG
technology, write a program which uses an algorithm to modify heart rate data,
connect to Kubios Cloud for detailed analysis and to create an easy-to-use
interface to show stress levels and recovery and to improve students' technical
and teamwork skills through project management.


## 2 Theoretical Background

This section explains the basic ideas behind the project to help readers
understand heart rate measurements and the sensor used in the project.

Heart rate is the number of times your heart beats in a minute, and it is measured
in beats per minute (bpm). Heart rate variability (HRV) is the difference in time
between heartbeats, measured in milliseconds (ms). HRV can give us information
about stress and recovery levels in our bodies.

There are two main parts of the body's control system that affect heart rate and
HRV. One part helps us react quickly in stressful situations, and the other part
helps us relax and recover. HRV shows the balance between these two parts.

Normal heart rate values are different for each person. For example, adults
usually have a resting heart rate between 60 and 100 bpm, but athletes might
have lower heart rates. HRV values also change depending on things like age,
how fit you are, and your health. The project uses a special kind of sensor that
measures blood flow changes by looking at how light is absorbed in the body's
tissue. This sensor sends light into the tissue and then measures the light that
comes back. By looking at the changes in the light, the sensor can measure heart
rate and HRV.



## 3 Methods and Material

This section discusses how the heart rate detection and analysis system project
was carried out, focusing on the materials used and the testing process. The
project aimed to create a program that uses photoplethysmography (PPG) to
measure heart rate and its variability. The gadget operates by sensing the
volumetric blood changes in the tissue's microvascular bed optically and
identifying the peaks of the alternating signal.

To accomplish this goal, the project utilized various materials, including a sensor,
software, and devices. The technique used was photoplethysmography (PPG), a
technology that optically measures changes in blood volume in the blood vessels
of tissue. The software used included Kubios Cloud HRV analysis service, which
provided a more in-depth HRV analysis after sending the user’s heart rate data
to the server.

Metropolia University of Applied Sciences’ teaching personnel and senior students
evaluated and chose the hardware for the project as well as created a special
board for the development of IoT devices with the Raspberry Pi Pico.

The device used in the project was Raspberry Pi Pico W. The Raspberry Pi Pico
W (Figure 1) is a low-cost microcontroller board, designed for high-performance
microcontroller applications. The Pico W is the wireless version of the Pico,
featuring built-in support for Wi-Fi and Bluetooth connectivity. The Pico W is built
around the RP2040 microcontroller, which is a dual-core ARM Cortex-M0+
processor running at 133MHz. It has 264KB of on-chip RAM and 2MB of on-board
flash memory for program storage. The board also features 26 GPIO
multifunction pins, which can be used for a wide variety of purposes, including
connecting sensors and other hardware components. The rotary encoder with a
push button on the special board was used for different operations of the
program.

<img width="500" alt="21" src="https://github.com/MuathOthman/Healthify/assets/111856849/d683025c-6eaf-49f4-acfc-569a5d69a525">

Figure 1. The Raspberry Pi Pico board

The Pico W's wireless capabilities are provided by the onboard ESP32-S2 module,
which provides support for Wi-Fi 802.11 b/g/n and Bluetooth 5.0. The board also
features a Micro-USB port for power and data, as well as a built-in voltage
regulator to ensure stable operation. During the project, the Pico W was used to
interface with the photoplethysmography sensor and process the data to
calculate heart rate and heart rate variability. The Pico W's GPIO pins were used
to connect to the sensor. 

The heart rate sensor operates on a voltage of 3-5 V and was connected to the
Pico via the Grove connector. The Crowtail Pulse Sensor v2.0 (Figure 2) which
has 4 pins was used to detect the user's heart rate, utilizing its LED, photodiode,
analog amplifier, and analog signal output. The finger is pressed on top of the
sensor. The Crowtail board has a LED in the middle that sends light into the body
tissue. Below the LED is an optical sensor called a photodiode that detects the
reflected light and turns it into a voltage signal. (Figure 2) The AD-converters
were used to convert the analog signal from the heart rate sensor to digital. The
preprocessed pulse data was wirelessly sent to a computer, which then sent the
data to the web server. The analysis results were returned to the development
board and displayed on the 128x64 OLED display.

<img width="500" alt="22" src="https://github.com/MuathOthman/Healthify/assets/111856849/bc921998-06e1-4b00-b113-849f85a3b1a2">

Figure 2. Crowtail pulse sensor v2.0. The measuring LED on the left and on the right is
an optical sensor.

To verify that the system produced valid readings for the measured parameters,
the heart rate was also compared to a professional heart rate monitor to ensure
accuracy and reliability. Approximately, half of the time was used for creating the
program and the other half was purely used for testing. Overall, the Raspberry
Pi Pico W was well-suited to the requirements of the heart rate detection and
analysis system project and its wireless connectivity made it an ideal choice to
be used in the project environment.

## 4 Implementation

The final end-to-end system of the project consists of various components
working together. The microcontroller used is the Raspberry Pi Pico W, which is
connected to a heart rate sensor through a grove connector. The microcontroller
is connected to a PC using a micro-USB cable. Then there is a wireless connection
between the computer and the Raspberry Pico. Once the data is received by the
PC, it undergoes the program made for it, including calculations of moving
average and intervals. The processed data is then sent to a KubiosCloud server,
which performs further analysis. The final results are then sent back to the
computer, where they are displayed on the OLED display via the microcontroller.
(Figure 3)

<img width="600" alt="Picture 11" src="https://github.com/MuathOthman/Healthify/assets/111856849/e3e78274-3cf9-408b-9dcb-decb1c81138f">

Figure 3. The end-to-end system of the final product. The system has four parts. From
the right, a heart rate sensor, a microcontroller board Raspberry Pi Pico W with an
interface screen, user‘s computer with the program code and a cloud service for data
analysis.

The OLED screen in this project serves as a user interface where the user can
operate the menu by using the rotary switch with a push button. When the user
presses the "heart rate" section of the menu with the rotary encoder button, they
are prompted to place their finger on the heart rate sensor, and the real-time heart rate is displayed on the OLED screen. The program calculates 20 pulses
and sends them to the KubiosCloud for further analysis. When the user wants to
return to the menu, they can press the middle button of the three LED controller
pins. When the user presses the “Analysis” section of the menu, the user can see
their stress and recovery indexes calculated from the previous heart rate
measurements. This feature provides the user with insights into their stress levels
and the effectiveness of their recovery practices. These measurements are the
parasympathetic and sympathetic measurements of the nervous system.

The algorithm uses an analog input on pin 26 to read sensor values at a frequency
of 250 Hz. These sensor values are then stored in a FIFO buffer with a capacity
of 750. The algorithm then calculates the moving average of the sensor values
and checks if the average falls within a pre-defined range of peak values (36000
to 37000). If the average falls within this range, the algorithm detects a peak and
calculates the time difference between the current and previous peak. If the time
difference is greater than 500 milliseconds, the heart rate is calculated as 60,000
divided by the time difference in milliseconds. The heart rate is then displayed
on an OLED screen and printed to the console
