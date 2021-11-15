---
layout: home
permalink: index.html
repository-name: e14-3yp-Telepresence-Robot
title: Telepresence Robot
---
# Telepresence Robot
## Team
-  E/14/262, Sanoj Punchihewa, [e14262@ce.pdn.ac.lk](mailto:e14262@ce.pdn.ac.lk)
-  E/14/305, Chandima B Samarasinghe, [e14305@ce.pdn.ac.lk](mailto:e14305@ce.pdn.ac.lk)
-  E/14/337, Yuvini Sumanasekera, [e14337@ce.pdn.ac.lk](mailto:e14337@ce.pdn.ac.lk)

## Table of Contents
1. [Introduction](#introduction)
2. [Solution Architecture](#solution-architecture )
3. [Hardware & Software Designs](#hardware-and-software-designs)
4. [Conclusion](#conclusion)
5. [Links](#links)

---

## Introduction

A telepresence robot is a mobile, remote-controlled device that enables a person to be virtually present and to interact in a remote place. This project will be based upon developing such a robot for the department. With the use of interactive elements such as high definition audio and video, the robot will allow users (students/staff) to collaborate in person and remotely.


## Solution Architecture

EMBEDDED SYSTEMS DESIGN

 

1. What will you be measuring and/or controlling?

 Measuring/Inputs

Ultrasonic Sensor: to measure the distance to the nearest obstacle in front of the robot.
GPS Sensor: to track the robots position (assuming general purpose usage of the robot other than using inside the department)
Microphone: to input voice signals.
Web camera: to input video signals.
Controlling

Motor Controllers: to control the robots movement
Servo Motor: to change the angle of the (camera+LCD screen)
2. What embedded systems platform(s) will you be using, and why?

 Raspberry Pi 3 Model B

To implement the controlling logic and all the softwares we are going to use high level programming languages such as Java and Python. It is required to choose a microcontroller capable of installing a OS like Linux.
Has an inbuilt Wifi module.
To control motor controllers, servos, ultrasonic sensors and other peripherals the raspberry pi has about 40 GPIO pins.
To do real time full-duplex video+audio streaming, microcontroller with a high performance CPU is required.
The robot includes a LCD screen. The cheap microcontrollers such as Arduino are not capable enough to produce required minimum frame rate, while the raspberry pi has dedicated GPU. Having a raspberry pi cut off the extra GPIO pin requirements of connecting the LCD as well.
 3. How does the system connect to the network?

 Primary:

Using the inbuilt Wifi module, the robot will connect to the available department’s Wifi router to get access to the internet.

 

Secondary:

If for some reason Wifi is not available, the robot will connected to the internet using the GSM (module).

 

Users:

Users connect to the network using their END devices. 

 

4. What peripheral components will you be using, and how do they work?

 

LCD Screen

LCD screen will use to display the video of the user and to display the relevant information. This display will connect through the HDMI port of the raspberry pi. Power will be given through a suitable voltage regulator.    

 

Motor Controller (BTS7960 43A, Type: IBT_2) x 2

Motors will draw huge current when in operation. In order to avoid drawing that current from the microcontroller pins these motor controllers are used. Motor controllers get power from the external power source and drive the motors according to the given signals by the GPIO pins connected to the microcontroller.

   

Servo

A servo is connected to the head section of the robot to change the angle of the head section (LCD+Camera+Mic…). Control signals to this servo is given through the GPIO pins and the power source is connected through a 6V voltage regulator.

 

Ultrasonic Sensor (HC-SR04)

Used to get the distance measurement to the nearest obstacle in front of the robot. Connected via the GPIO pins. Normally working current of these module is 15mA. Since the maximum current of a GPIO pin signal is 16mA (recommend 8mA), to be safe this module will also powered by the external power source through a 5V voltage regulator and only the control signals will give through GPIO pins.

 

GSM module

Will be using as the secondary method of connecting to the network. Control signals will give through GPIO pins. Power will give through a voltage regulator.

 

GPS module

Used to get the location data. Will connect through the GPIO pins. Power will be given through a suitable voltage regulator.

 

Inbuilt WiFi module

Primary method of connecting to the network.

 

Web Camera

Used to get the video input. Connected through the USB port of the raspberry pi.

 

Speaker

Will connect through the audio connection of the raspberry pi

 

Mic

Since there is no separate connector in raspberry pi to connect a mic, USB extension module will be used to connect a microphone to the raspberry pi.

 

## Hardware and Software Designs

![image](https://user-images.githubusercontent.com/73756777/120496303-14412580-c3db-11eb-8b82-c84132aa0a89.png)
![image](https://user-images.githubusercontent.com/73756777/120496370-2327d800-c3db-11eb-8be0-50f0d2bf2d5b.png)
![image](https://user-images.githubusercontent.com/73756777/120496394-28852280-c3db-11eb-9e44-5650c0d07b41.png)
![image](https://user-images.githubusercontent.com/73756777/120496684-641fec80-c3db-11eb-86da-f228b5879483.png)
![image](https://user-images.githubusercontent.com/73756777/120496702-684c0a00-c3db-11eb-9c2d-60d84346cbe8.png)
![image](https://user-images.githubusercontent.com/73756777/120496817-831e7e80-c3db-11eb-985b-282347ba6d6d.png)


## Conclusion
#Issue

Eventhough we successfully tested the peer-to-peer video streaming using default browser applications when it comes to integrating that into our java program we got to know that all the regular web components that we can use with java are not given permission to access resources like camera by the base implementation. Therefore, we have checked for the alternative web components and got to know that the only opensource web controller we can use with java is the CEF browser (chromium, JCEF) component. But, we had to build that from the source files before integrating that in our program. Eventhough, we were able to build that and run on amd64 architecture , we haven't found clear explanations or successfull builds (or build methods) for arm architecture. Therefore, it seems to be integrating a browser component which can access to cameras in the java application itself seems to be rather difficult (or impossible) task.

[we have used raspbian os in raspberry pi 3 b]

#Possible Solutions

01) Opening the video streaming mode using a regular browser (only for the video streaming mode)

02) Using a different platform : (Android Things)

The browser component we normally used in android application development can access to the resources like cameras. Therefore, we though of using android things os as our base os in our raspberry pi. Since, we are already familier with android application development we can develop the an andorid application for the bot.

#The Solution we are currently working on : 2nd solution.

## Links

- <a href = "https://github.com/cepdnaclk/e14-3yp-Telepresence-Robot" target = "_blank"> Project Repository </a>
- <a href = "https://cepdnaclk.github.io/e14-3yp-Telepresence-Robot/" target = "_blank">Project Page</a>
- <a href = "http://www.ce.pdn.ac.lk/" target = "_blank">Department of Computer Engineering</a>
- <a href = "https://ce.pdn.ac.lk/" target = "_blank">University of Peradeniya</a>



[//]: # (Please refer this to learn more about Markdown syntax)
[//]: # (https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
