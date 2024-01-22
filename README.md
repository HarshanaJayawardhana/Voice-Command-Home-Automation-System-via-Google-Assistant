# Introduction 
### 1.1 Overview of the chapter

Home automation is a primary growing industry that can change people's lifestyles. Some of these home automation systems target those looking for luxury and modern home automation platforms; others target people with special needs, such as the elderly and the disabled. The standard wireless home automation system allows one to control household appliances from a wireless centralized control unit. These devices are usually compatible with each other and with the control unit for most commercially available home automation systems. The developed system can be integrated as a single portable unit to wirelessly or wire control lights, fans, televisions, air conditioners, electric doors, etc., and enable or disable any equipment.<br>

The problem is usually with older people or people with disabilities who may not be able to move and who may need outside help. People living alone may need help at home. Therefore, a home automation system for voice control has been developed that allows users to perform specific tasks using their voices. The system is designed to sputter with a portable device (remote). Commands otherwise, they have to go to the microphone to speak. Having a remote will make the portable and system more user-friendly.<br>

Voice Controlled Wireless Home Automation is Internet / Bluetooth / Wi-Fi is a project integrated with mobile phones (application) to facilitate the elderly and the disabled so that home utilities can be easily controlled via their phone and voice command. <br>

The system is an intelligent home connected to the internet, allowing the user to access the home securely and remotely control the temperature, lighting, and household appliances. The internet of things is the most critical technology for making a smart home. It can connect and control everything to access remotely anytime and anywhere using the internet. IoT (Internet of Things) is the environment in which physics interact, enabling computer communication from user to the machine and machine-to-machine communication, which extends to things. IoT devices can exchange content based on controlling activism in a specific way. The advantage of IoT networks is that data can be separated and created by naming, filtering, manipulating, and extracting data. Authorities forecast that by the end of the year, by 2020, about 50 billion devices will have an Internet connection. The system is designed to be easy to carry, install, configure, operate and maintain by a non-technical person. Illustration of IoT is shown in Figure 01.
<br>
<br>
<img src="Document/Images/01 Illustration of IoT.png" width="700" >
###### Figure 01: Illustration of IoT
<br>
<br>

### 1.2	Aim and objectives
-	To control all component of the house via cloud.<br>
-	To control all component on master circuit.<br>
-	To increase efficiency and decrease effort.<br>
-	To achieves simplicity<br>
-	To give user friendly interface for user.<br>


# Methodology
### 2.1	Overview of the chapter

In a methodology part include six the sub part such as the concept behind the proposed design, requirement components, hardware design, graphical user interface (GUI) design, creating Adafruit IO project and connecting to Google assistant through IFTTT. Which mentioned sub parts includes method that how to develop the project and what are the components that used in the projects and how use components in project. Include PCB diagram of the system. Step of developing are also described.  

### 3.2	Concept behind the proposed design  
The proposed project aims to control several home appliances by receiving and following the voice command from the user through Google Assistant. The command is interpreted from the mobile phone and sent to IFTTT by Google Assistant. IFTTT acts as a central means of communicating with the user equipment. It sends the signals to the ESP 12e chip, which sends the signal to the control microcontroller (ATMEGA 328p for saving data, displaying the data, and connecting with the switch).<br> 

The control microcontroller is programmed to send the data to the solid-state relay board, including the microcontroller. The switch controls light and fan without voice command and cloud support. All switch sets connect with the control microcontroller via I2C communication. An LCD screen is interfaced to show the commands received by the user and make it easy when troubleshooting is required. The voice command home automation system requires 5V power, which switched-mode power supply technology in this project. The proposed project block diagram is shown in below Figure 02.
<br>
<br>
<img src="Document/Images/02 Proposed project block diagram.png" width="700" >
###### Figure 02: Proposed project block diagram
<br>
<br>
However, the system had to be modified due to problems with the proposed project and the improvement idea. Using a wire communication method with a wireless communication method, using a pc-based GUI instead of an LCD, installing an energy consumption system, and increasing the operating voltage are the main ones. Modified project block diagram is shown in Figure 03.
<br>
<br>
<img src="Document/Images/03 Modified project block diagram.png" width="700" >

###### Figure 03: Modified project block diagram
<br>
<br>

### 2.3	Hardware design 
A printed circuit board is a rigid structure. It contains electrical circuitry made of embedded metal wires known as traces and large areas of metal called planes. The electronics are soldered to the dashboard's top, bottom, or both layers on metal pads. These pads are connected to the board circuit. Therefore, it allows the components to be connected. The board consists of a single layer in one circuit, an upper and lower circuit, or several layers of circuits stacked together. <br>

Several printed circuit boards were used for ease of installation, complexity reduction, troubleshooting, and improvement for this project. All circuit boards were designed by Autodesk Eagle and designed as single-layer circuits.

#### 2.3.1 Power Supply Circuit
The power supply of a project is the foods that enable our electronic components to work as desired. Even for experienced manufacturers, choosing the proper power supply is a necessary process that must be done carefully. This project uses 12 voltages and 1 ampere SMPS to power up the project. It is based on DK112 Power Management IC.<br>

Before creating the prototype, we will explore the 12v SMPS circuit diagram and its functionality. The circuit has the following sections;
-	SMPS fault protection<br>
-	AC-DC conversion and PI filter<br>
-	Switching circuit<br>
-	Clamp circuit<br>
-	Magnetics and galvanic isolation<br>
-	Secondary Rectifier and Filter Section<br>
-	Feedback section.<br>

**SMPS fault protection** This section consists of one component, R1. R1 is a 0.1Ω 1/2W resistor used to save SMPS circuits during severe ampere damage. If the circuit takes more amperage, the fuse resistor will damage, and other power supply components will save.

**AC-DC conversion and PI filter** This AC-DC conversion section is governed by the four 1N4007 diodes (D1 – D4). The PI filter is designed to reduce common-mode EMI rejection. This section is created using C1 and L1. C1 is a 400V 10uF capacitor. L1 is a common mode of choking mode that takes a differential EMI signal to cancel both.

**Switching circuit** It is the heart of an SMPS. The switching IC DK112 controls the transformer's primary side. The switching frequency is 65 kHz. Small transformers can be used due to this high switching frequency. 


**Clamp circuit** D5, C2, and R2 are the clamp circuit. The transformer acts as a massive inductor across the power driver IC DK112. Therefore, during the inactive cycle, the transformer generates high voltage coils due to the leakage induction of the transformer. The clamp circuit suppresses these high-frequency voltage spikes across the transformer. 

**Secondary Rectifier and Filter Section** The output from the transformer is rectified using Schottky rectifier diode D6 and converted to DC. The filter section consists of a filter capacitor C5. It has a lower ESR capacitor for better wave refraction. Also, an LC filter using L2 and C6 provides better ripple rejection across the output.


 
**Feedback section** The PC817 optocoupler senses the output voltage. Furthermore, it acts as galvanically isolating the secondary feedback sensing portion with the primary side controller. The optocoupler has a transistor, and an LED inside. The transistor is controlled by controlling the LED. Communication is done visually, so it has no direct electrical connection. Therefore, the galvanic isolation of the feedback circuit is also satisfactory. The PCB layout of the power supply circuit is shown in Figure 04.
<br>
<br>
<img src="Document/Images/04 PCB layout of the power supply circuit.png" width="700" >
###### Figure 04: PCB layout of the power supply circuit
<br>
<br>
 
#### Magnetics and galvanic isolation
High-frequency transformers transfer electric power. The physical size depends on the power to be switched and the operating frequency. The higher the frequency leads to the smaller the physical size. Frequencies are typically between 20 kHz and 100 kHz. Ferrite is used as the primary material. The transformer is ferromagnetic. It converts the high voltage AC to a low voltage AC and provides galvanic isolation. E core transformer was used for transferee power in this circuit. All of the parameters are shown in Figure 05 for transformer winding. 
<br>
<br>
<img src="Document/Images/05 Circuit power supply transformer calculation.png" width="700" >
###### Figure 05: Circuit power supply transformer calculation
<br>

#### 2.3.2 Master Circuit
This circuit was introduced to control all other devices in the system and save their parameters and statements separately. The PCB layout of the master circuit is shown in Figure 06.
<br>
<br>
<img src="Document/Images/06 PCB layout of the master circuit.png" width="700" >

###### Figure 06: PCB layout of the master circuit
<br>
It has two communion types for communicating with each other: RS – 485 and Serial. RS 485 is an industrial specification. It defines the electrical interface and physical layer for point-to-point communication of electrical devices. The RS-485 standard allows for longer cable distances in an electrically noisy environment. In addition, it can support multiple devices on the same bus. Serial communication is a communication method that uses one or two transmission lines to send and receive data. That data is continuously received and sent one bit at a time. However, it consists of four microcontrollers, and their functions are as follows,
<br><br>

- **Local Host microcontroller** This microcontroller is ESP12E and was used to send data packets for wireless modules. Data was sent via ESP-NOW and programmed by Arduino IDE. ESP-NOW is a low-power, secure, and direct wireless communication protocol that enables multiple ESP devices to communicate with each other without the need for Wi-Fi or a router. It allows low overhead peer-to-peer wireless data transfers but in small packets. Maximumly 250 bytes of data can be exchanged. It is a fast and easy communication protocol for transmitting small amounts of data. The project's GUI allows the local host microcontroller to change its parameters and devices.<br>

-	**Cloud communication microcontroller** This microcontroller is ESP12E and maintains a connection with Wi-Fi and Adafruit. Before the program ESP12E microcontroller, it registered in the Adafruit and needed to get an API key. The project's GUI allows the microcontroller to change its Wi-Fi settings.

-	**Memory save microcontroller** This microcontroller is ATmega328p, and it works as memory. It saved all address parameters and statements separately in microcontroller EEPROM. It provides the system with the data it needs at start-up time and keeps in mind the changes in addresses that occur when the system is running.

-	**Wired devices Control microcontroller** This microcontroller is STM32, and it maintains a communication relationship with the all wire device, display module, and above microcontroller as one system. It has 20KB SRAM, and it is helpful to save system statements separately during the running time. If any command was come by GUI or Adafruit, the microcontroller determines which devices the command is sent to. Nevertheless, it has no EEPROM for saving parameters and statements. As a solution, a microcontroller with an EEPROM is mounted on the inside of the master circuit.

#### 2.3.3	Display Controller Circuit
The main circuit communicates data through the bus communication so it cannot be read by a computer. This circuit work as the bus to USB converter. Another function is the ability to read sensor data. CH340E USB to TTL converter was used to connect with the computer. The PCB layout of the Display Controller Circuit is shown in Figure 07.
 <br>
<br>
<img src="Document/Images/07 PCB layout of the Display Controller Circuit.png" width="700" >

###### Figure 07: PCB layout of the Display Controller Circuit
<br>

#### 2.3.4	Power Analyser Circuit
 The power utilized in homes is usually produced by electric generators or renewable energy sources (Solar energy, Wind energy, Hydropower, etc.). It is then supplied to homes and industries through the power grid. A power analyser can measure and monitor the flow of energy in AC power. Several parameters in the AC can be detected, such as Voltage, Current, Watts (joules per second), frequency of the power line, and power factor. Several sensors were used to obtain the above parameters, such as the ZMPT101B voltage sensor, 20A / 5mA current sensor, and PC817 optocoupler frequency sensor. The voltage sensor and the current sensor operate linearly. The PC817 optocoupler detected the line frequency, and the ATmega internal clock was used to measure the pulse width of the frequency. <br>
The microcontroller is programmed at a sample rate of 100ms. The average rate is set so the user can change it via GUI. Its other function is to introduce overload, high frequency, voltage, current protection, and low voltage and frequency protection. If any protection is turned on, the home power supply will be switched off via a contactor. PCB layout of the power analyser circuit is shown in Figure 08.
 <br>
<br>
<img src="Document/Images/08 PCB layout of the Power Analyser Circuit.png" width="700" >

###### Figure 08: PCB layout of the Power Analyser Circuit
<br>

#### 2.3.5	Wire Light Circuit
This circuit was introduced to control wires such as panel lights and LED tube lights. It requires two pairs of wires as power lines and a signal bus line. The light drive should be adjusted according to the number of watts in the bulb and is controlled by an N channel MOSFET. The advantage is that it can control most of the lights separately with less wire. It is based on an ATtiny85 microcontroller and uses a RS 485 IC for communication. The circuit has an address in the control device's microcontroller and is saved in the EEPROM. It can be done through the GUI if needed to change the address somehow. PCB layout of the Wire Light Circuit is shown in Figure 09. 
<br>
<br>
<img src="Document/Images/09 PCB layout of the Wire Light Circuit.png" width="700" >

###### Figure 09: PCB layout of the Wire Light Circuit
<br>


#### 2.3.6	Wireless Light Circuit
This circuit was introduced to control wireless lightings such as panel lights, LED tube lights, or LED pendant lights. Unique about this is that it only requires a power connection. Like the circuit above, the light drive should be adjusted according to the number of watts in the bulb and is controlled by an N channel MOSFET. It is based on an ESP01 Wi-Fi module. To control this, the mac address is used instead of the address, which is assigned to the system through the GUI. The user is allowed to change the address through the device manager interface. PCB layout of the wireless light circuit is shown in Figure 10.
<br>
<br>
<img src="Document/Images/10 PCB layout of the Wireless Light Circuit.png" width="700" >

###### Figure 10: PCB layout of the Wireless Light Circuit
<br>

### 2.5	Graphical User Interface design
Graphical User Interface is an interactive visual component system for computer software. Creating a Graphical User Interface allows a user to interact with an electronic device through images rather than plain text commands. The GUI displays device information and represents actions the user can take.<br>

Creating a GUI is user-friendly; there are different elements and objects that the user uses to interact with the software. This project used visual studio 2015 community software to design Graphical User Interface. Several visual programming languages with unique advantages for developing a graphical user interface design, such as Python, HTML5/JavaScript, C, C++, and C#. C# may be considered preferable options due to their ability to run GUIs simultaneously in a desktop application. <br>

This project GUI was created as the one exe file and should be installed on the computer. It has several interfaces to communicate with the user. This GUI can run on any laptop, desktop, or industrial PC with the following 32nit or 64-bit operating system; Microsoft Windows 10 All editions, Microsoft Windows 10 All editions, Microsoft Windows 8 All editions, Microsoft Windows 7 All editions with Network framework 3.5 or above. Moreover, CH340E USB to TTL Serial Converter drivers are required because this GUI communicates with the system via a serial port. However, it consists of seven pages, and their functions are as follows,<br>

#### 2.5.1	Start-up Interface
This interface works as starting interface (Figure 11). The GUI communicates with the system via the display module based on the interface data. This interface supports changing several serial connection settings such as serial port, serial baud rate, serial data bits, and serial stop bits. The parameters mentioned above are automatically filled in based on past data, giving the user the ability to make changes if they need to for any reason. However, logging in to the system without a password is not allowed. The user is allowed to change the password in the settings interface.
<br>
<br>
<img src="Document/Images/11 Start-up Interface of home automation system.png" width="700" >

###### Figure 11: Start-up Interface of home automation system
<br>
 
#### 2.5.2	Main view Interface
This interface works as the primary interface when the system is running. This interface represents memory data at starting time and allows the user to make changes if the user needs to for any reason. The interface includes the real-time date, power analyser, temperature and humidity, a power warning message, and visual light control switch. However, The Exit button is activated only when logged into the system via the settings interface. The main parts and their functions are described below.<br>

 -	This interface displays the current time and date and retrieves the data from the computer clock. Making any changes to the time on the computer directly affects the interface.<br>
 
 -	Another function of this interface is a digital power meter representing line voltage, line current, line frequency, and line power. Moreover, it shows warning messages when it is lower and higher than the pre-set values in line voltage, line current, and line frequency.<br>
 
 - Another function is visual light control switching and represents their statements via GUI. In this interface, it is activated based on the light's address, and there are three activation modes. At start-up, the button is shown in blue, and the color change is based on system data. In the first mode, the button turns green, indicating that the bulb is OFF. In the second mode, the button turns red, indicating that the bulb is ON. In the third mode, the button turns yellow, indicating that the bulb is connected with the PIR sensor and works with PIR sensor commands. Then when the button is pressed again, it goes back to the first mode.<br>
 
 -	The interface's final function is to represent the average humidity and temperature separately. This requires three temperature sensors and a humidity sensor. However, it is not included in this project, and the necessary coding is available in the interface and display module.<br>

Main view Interface of home automation system is shown in Figure 12.
 <br>
<br>
<img src="Document/Images/12 Main view Interface of home automation system.png" width="700" >

###### Figure 12: Main view Interface of home automation system
<br>

#### 2.5.3	Button mode interface
This interface was introduced to control the light and represent their statements with their locations. It has an only button to control light statements. Its functionality and mode variation are similar to the main view interface. However, the location label on the buttons is particular. Button mode interface of home automation system is shown in Figure 13.
<br>
<br>
<img src="Document/Images/13 Button mode interface of home automation system.png" width="700" >

###### Figure 13: Button mode interface of home automation system
<br>

#### 2.5.4	Energy consumption interface
This interface introduced to represents the energy consumption data. It has digital power meter and gauge meter for represents line voltage, line current, line frequency and line power. The energy consumption interface has a chart with four options, which calculate the current power consumption and display each mode. For example, if click on ‘TODAY’, Power consumption is calculated separately according to the number of hours used. Energy consumption interface of home automation system interface is shown in Figure 14.
<br>
<br>
<img src="Document/Images/14 Energy consumption interface of home automation system.png" width="700" >

###### Figure 14: Energy consumption interface of home automation system
<br>

#### 2.5.5	Schedule Devices interface
This interface introduced to schedule the devices according time. This means that the device is automatically controlled for a pre-set period of time. The light address, light turn ON time, and light turn OFF time were requested separately by the GUI. The check box will tell if the schedule should be executed according to the pre-set data. And it can be changed very quickly by the user. The below buttons in the interface give the user the opportunity to enter new data, modify existing data and delete data. This function is best to turn off the outdoor light automatically. Schedule Devices interface of home automation system is shown in Figure 15.
<br>
<br>
<img src="Document/Images/15 Schedule Devices interface of home automation system.png" width="700" >

###### Figure 15: Schedule Devices interface of home automation system
<br>

#### 2.5.6	Devices manager interface
This interface introduced to management the device address and MAC address.  Wire device address changing can be done by providing the current address and the new address. The below buttons in the interface give the user the opportunity to add new wireless devices, modify existing wireless devices and delete wireless devices. Changes made to wireless devices are sent to the local host folder memory. When calling wireless devices, only the address is addressed and the local host sends the data to the corresponding mac address. Devices manager interface of home automation system is shown in Figure 16.
 <br>
<br>
<img src="Document/Images/16 Devices manager interface of home automation system.png" width="700" >

###### Figure 16: Devices manager interface of home automation system
<br>

#### 2.5.7	Setting interface
This interface introduced to change the setting parameter in the home automation system. It is mandatory to log in before changing the settings here. It has several settings and a brief description of them is given following;

-	General settings - It support to the change LOG IN and Start-up password. This allows the user to change the data sampling rate of the analysis. Finally, Can disable the function in the GUI as shown in the image below.
-	Analysis related settings - It support to the change Analysis related setting such as analysis calibration setting, power warning massages setting and power protection cut off setting. The following figure shows the adjustable parameters mentioned above.
-	Communication settings - This shows data about the serial pot and is not allowed to be modified. And this is used to send data about Wi-Fi setting to the master circuit
-	Temperature settings - This does not apply to this project and is built on future works.  It is used to send data related to HVAC system control.

The setting interface of home automation system is shown in Figure 17.
<br>
<br>
<img src="Document/Images/17 The setting interface of home automation system.png" width="700" >

###### Figure 17: The setting interface of home automation system
<br>


### 2.6	Creating the Adafruit IO project
Adafruit IO can be defined as free cloud-based software built around the MQTT protocol. It supports creating many application projects where users can manage their projects over the internet. For the user, it becomes highly interactive and easy to use this application to manage any appliance from anywhere in the world over the internet. Other software features include real-time representation of project data through a visually pleasing dashboard. The user can display charts, graphs, and data, for example, sensor readings.
Adafruit IO was required as a web service link to communicate with IFTTT. First, create an account in Adafruit IO and create a feed that suits the project.

-	Step 01 - Visit [io.adafruit](https://io.adafruit.com/) in the browser search app. Then its main page will look like the Figure 18 below. Then click on the Get started for Free button highlighted in the picture.
<br>
<br>
<img src="Document/Images/18 Main page of the Adafruit IO.PNG" width="700" >

###### Figure 18: Main page of the Adafruit IO
<br>


-	Step 02 – After that, it will be asked for the data required to create an account, provide it accordingly, and click 'create an account.' The creating account window in Adafruit is shown in Figure 19.
 <br>
<br>
<img src="Document/Images/19 Account creating window in Adafruit.PNG" width="700" >

###### Figure 19: Account creating window in Adafruit
<br>


-	Step 03 - A new window will open after signing in with the created account. It will consist of the dashboard. Click 'Feeds' and then Click 'view all' to continue creation, as shown in Figure 20 below. 
 <br>
<br>
<img src="Document/Images/20 Feeds window in Adafruit IO.PNG" width="700" >

###### Figure 20: Feeds window in Adafruit IO
<br>

-	Step 04 – Click the 'New Feed' button to create a new feed in the Feeds window. Give the feed's name as 'Home Automation' and give a description only if necessary. Then click 'Create' to proceed. Below Figure 21 shows a window of the feed created. 
 <br>
<br>
<img src="Document/Images/21 Feeds create a window in Adafruit IO.png" width="700" >

###### Figure 21: Feeds create a window in Adafruit IO
<br>


-	Step 05 – Finally, taking the Adafruit IO key is necessary to program the cloud communication microcontroller in the primary circuit. Click on the 'My Key' in the Adafruit IO to get it. After the click, the AIO key can be getting through the new window (Figure 22).

 <br>
<br>
<img src="Document/Images/22 Adafruit IO key window in create account.PNG" width="700" >

###### Figure 22: Adafruit IO key window in create account
<br>


### 2.7	Connecting to Google Assistant through IFTTT
In this project, one of the objectives is to control the house appliances through voice commands. Thus, after setting up project Adafruit IO feeds, the next step is integrating Google Assistant into Adafruit IO. It allows controlling home appliances with voice commands. 

As mentioned previously, the IFTTT service was used to configure the trigger for the home automation system. IFTTT is a short word for If This Then That, which is the best way to integrate apps, devices, and services. IFTTT is an open-source service that gives the user the freedom to program a response to an event according to user likes. 

-	Step 01 - Even if the IFTTT service was used as free, the account was needed to create. Visit [ifttt.com](https://ifttt.com/) in the browser search app. Then its main page will look like Figure 23. To create the account in the IFTTT, click 'Get started'.   
<br>
<br>
<img src="Document/Images/23 Main page of the IFTTT.PNG" width="700" >

###### Figure 23: Main page of the IFTTT
<br>

-	Step 02 – There are three options (Apple, Google, or Facebook) to connect with IFTTT or can 'sign up' with own given email. Click 'sign up' to create an account. Figure 24 shows the get-start window.
<br>
<br>
<img src="Document/Images/24 Get the start window of the IFTTT.PNG" width="700" >

###### Figure 24: Get the start window of the IFTTT
<br>

-	Step 03 – Enter the email address and password to create an account on IFTTT, as shown in Figure 25.
<br>
<br>
<img src="Document/Images/25 Sign up window of the IFTTT.PNG" width="700" >

###### Figure 25: Sign up window of the IFTTT
<br>

-	Step 04 – Then, create a project applet. After creating the account, creating Project Applet page will open automatically. Click on ‘Create’ to create an applet. Figure 26 shows the create applet page get start window.
<br>
<br>
<img src="Document/Images/26 create an applet page of the IFTTT.PNG" width="700" >

###### Figure 26: create an applet page of the IFTTT
<br>

-	Step 05 – A new window will open, as shown in Figure 27. Click the 'Add' button in the 'If This' section to set up the applet.
<br>
<br>
<img src="Document/Images/27 create own applet page of the IFTTT.PNG" width="700" >

###### Figure 27: create own applet page of the IFTTT
<br>

-	Step 06 – Next page will open where we have to choose the project service (Figure 28). There are many options to choose from. Write down 'Google Assistant' in the search options bar and then click on its icon.
<br>
<br>
<img src="Document/Images/28 Choose a service window of the IFTTT.PNG" width="700" >

###### Figure 28: Choose a service window of the IFTTT
<br>

-	Step 07 – Then the page will open, which chooses trigger in googol assistant. Select ‘say a simple phrase’ (Figure 62) as this project trigger method.
<br>
<br>
<img src="Document/Images/29 Choose a trigger window of the IFTTT.PNG" width="700" >

###### Figure 29: Choose a trigger window of the IFTTT
<br>

-	Step 08 – A new window will open, letting specify the commands. This triggers when says "Ok Google" to Google assistant before a phrase you choose. For example, when you want to turn on the light in the kitchen at home, you just need to say, "Ok Google, turn on the light in the kitchen." There are several ways this can be done after the command. Can specify what to say to the assistant in the assistant Response Text box. After filling, click on 'Create trigger' to continue the setup applet. As shown in Figure 30, the form should be filled as in the example above.
<br>
<br>
<img src="Document/Images/30 Google assistant trigger filling window of the IFTTT.PNG" width="700" >

###### Figure 30: Google assistant trigger filling window of the IFTTT
<br>

-	Steps 09 – The below window will open (Figure 31). Click the ‘Add’ button in the ‘Then That’ section to set up the applet.
<br>
<br>
<img src="Document/Images/31 create own applet page with Then That in the IFTTT.PNG" width="700" >

###### Figure 31: Create own applet page with Then That in the IFTTT
<br>

-	Step 10 – Again page will open in which we will have to choose a project service. At this time, write 'Adafruit' in the search options bar and then click on its icon (Figure 32).

<br>
<br>
<img src="Document/Images/32 Choose a service page in Then That of the IFTTT.PNG" width="700" >

###### Figure 32: Choose a service page in Then That of the IFTTT
<br>

-	Steps 11 – Then, the page will open, which chooses trigger in Adafruit. Select 'Send data to Adafruit IO' as this project data sent method (Figure 33).
<br>
<br>
<img src="Document/Images/33 Choose a data sent method page in Then That of the IFTTT.PNG" width="700" >

###### Figure 33: Choose a data sent method page in Then That of the IFTTT
<br>

-	Steps 12 – A new window will open, specifying the code that should be sent to the project microcontroller via Adafruit after the Google assistant trigger. Adafruit account and Feed name will be filled automatically and if the Adafruit account has several Adafruit feeds, select the desired feed related to the project.

A code system has been introduced to suit the project when filling in the data to save. Take the code 'A41Z', for example. 'A' is the address, and the corresponding address number should be entered. 

Then, specify what to do for the device at the relevant address. Three numbers have been introduced for the three modes mentioned in the main view interface. '0' is the bulb off mode, '1' is the bulb light mode, and '2' is the mode controlled by the bulb PIR sensor. 

This applet is made to turn on the kitchen light, so the light address is set to '4' (according to the main view interface address), and the code required to turn it on is '1'. The code to turn off the kitchen light is 'A40Z'. The 'Z' is used to indicate the end of the code. The form is filled with the example given above in the figure below. Click 'Create action' to continue the setup applet (Figure 34).
 <br>
<br>
<img src="Document/Images/34 Send data to the Adafruit window of the IFTTT.PNG" width="700" >

###### Figure 34: Send data to the Adafruit window of the IFTTT
<br>

-	Step 13 – Click ‘Continue’ to continue the set-up applet, as shown in Figure 35.
<br>
<br>
<img src="Document/Images/35 Create your own window of the IFTTT.PNG" width="700" >

###### Figure 35: Create your own window of the IFTTT
<br>

-	Step 14 – The applet title will be displayed after the process. If required, the applet can be set to show a notification when activated. Click ‘Finish’ (as shown in Figure 36) to complete the process for the ‘turn on the light in the kitchen’ voice command.
<br>
<br>
<img src="Document/Images/36 Review and finish window of the IFTTT.PNG" width="700" >

###### Figure 36: Review and finish window of the IFTTT
<br>

-	Step 15 – The method can create several applets as defined above. After creating the applet, it can be checked by a phone with Google assistant. 



# Results and Discussion
### 3.1	Overview of the chapter
This main chapter's findings or the results obtained from simulation and experimental studies should be presented. Furthermore, the results obtained should be critically analysed. After that, the results' significance should be clearly stated in this chapter.

### 3.2	Experimental Results
Before building the project as a single system, the hardware function was tested separately, and the results are as follows;

#### 3.2.1	Google assistant results
As mentioned in the methodology, Creating several project applets. After creating the applet, it can be checked by a phone with Google assistant (Figure 37). Moreover, the data related to the tested applets are displayed on the feed page of Adafruit (Figure 38). The below Figures show the Google assistant and feed page of Adafruit IO after several times triggering Google assistant.
<br>
<br>
<img src="Document/Images/37 Google assistant after several times triggering..png" width="700" >

###### Figure 37: Google assistant after several times triggering
<br>

<br>
<br>
<img src="Document/Images/38 Feeds page after triggering Google assistant.png" width="700" >

###### Figure 38: Feeds page after triggering Google assistant
<br>

#### 3.2.2	Adafruit connection results
NodeMCU (inbuilt chip ESP12E) Board was used for the experiment. The USB powers the NodeMCU Wi-Fi board, and the program uploads to the board using the Arduino IDE. After the upload is complete, the Arduino IDE is a serial monitor displaying messages related to Google assistant. It attempts to be a part of the WLAN using the specific SSID and a password included in the configuration of the part of the program. It will show that the Wi-Fi is connected and the IP address of the NodeMCU board once the connection is confirmed. Then it tried to connect with the project Adafruit IO account and confirmed it. After connecting with the Adafruit IO account, it can use for data collection. The figure below shows print data on the NodeMCU. Results during the Adafruit connection test are shown in Figure 39.
<br>
<br>
<img src="Document/Images/39 Results during the Adafruit connection test.png" width="700" >

###### Figure 39: Results during the Adafruit connection test
<br>

#### 3.2.3	ESP-NOW connection results
This connection needs to control the wireless device via the system. Two NodeMCU (inbuilt chip ESP12E) Boards were used for the experiment. The USB powers the NodeMCU Wi-Fi boards, and the program uploads to the board using the Arduino IDE. One board is used as a data transmitter, and the other is the data receiver. This time no need for any kind of router and internet connection. After the upload is completed, the Arduino IDE is a serial monitor displaying messages as related send and receive data. Required NodeMCU Mac address before the ESP-NOW program. The figure below shows the Mac address from two of NodeMCU. ESP Board 01 MAC Address is shown in Figure 40 and ESP Board 01 MAC Address is shown in Figure 41.
<br>
<br>
<img src="Document/Images/40 ESP Board 01 MAC Address.png" width="700" >

###### Figure 40: ESP Board 01 MAC Address
<br>

<br>
<img src="Document/Images/41 ESP Board 02 MAC Address.png" width="700" >

###### Figure 41: ESP Board 02 MAC Address
<br>

Below, Figures 42 and 43 show print data from two NodeMCU.  Comport six works as a transmitter, and Comport eight works as a receiver.
<br>
<br>
<img src="Document/Images/42 ESP Board 01 results (transmitter).png" width="700" >

###### Figure 42: ESP Board 01 results (transmitter)
<br>

<br>
<img src="Document/Images/43 ESP Board 02 results (receiver).png" width="700" >

###### Figure 43: ESP Board 02 results (receiver)
<br>

#### 3.2.4	Power Analyzer results
A phototype power analyser was designed and tested before the power analyzer specified in the methodology was developed. A clamping and multi-meter were used to calibrate the analyzer and check the accuracy of the data obtained. The PC817 optocoupler detected the line frequency, and the ATmega internal clock was used to measure the pulse width of the frequency. The figures (Figure 44) below show the power analyzer's phototype circuit and the Arduino IDE's serial monitor result (Figure 45).  
<br>
<br>
<img src="Document/Images/44 phototype power analyser.png" width="700" >

###### Figure 44: Phototype power analyser
<br>

<br>
<img src="Document/Images/45 Results of power analyzer.png" width="700" >

###### Figure 45: Results of power analyzer
<br>

#### 3.2.5	ATtiny85 Bus communication results
This connection needs to control the wiring device via the system. ATtiny85 microcontroller and FT232RL USB to TTL Converter Boards were used for the experiment. The ATtiny85 microcontroller was p programmed using the Arduino Mega board with Arduino ISP. EEPROM was used to save the device address, and an experiment time, Arduino IDE, a serial monitor, was used command. It works at less than a 9600 baud rate. The light is controlled remotely using the Serial command is shown in Figure 46.
<br>
<br>
<img src="Document/Images/46 The light is controlled remotely using the Serial command.PNG" width="700" >

###### Figure 46: The light is controlled remotely using the Serial command
<br>

#### 3.2.6	PIR sensor results
A PIR sensor was used to control the light during the PIR mode. PIR sensor reading was checked separately before making it as a single circuit. The light is turned ON when it detects any motion in the environment. 
Furthermore, the microcontroller is programmed to turn off the light after one minute of the end of the motion. The result is shown in the Arduino IDE is a serial monitor. Phototype circuit is shown in Figure 47. Arduino IDE is a serial monitor result is shown in Figure 48.
<br>
<br>
<img src="Document/Images/47 phototype circuit.png" width="700" >

###### Figure 47: phototype circuit
<br>

<br>
<img src="Document/Images/48 Arduino IDE is a serial monitor result.png" width="700" >

###### Figure 48: Arduino IDE is a serial monitor result
<br>
 
### 3.3	Create Printed Circuit Board
The laser toner transfer technology was used to create the PCB layout developed in the above methodology. Art paper is used as printed paper. The PCB in the image below is developed here, and only two PCBs are manufactured as products because of their need to develop GUI and protocol. Master circuit with soldering parts are shown in Figure 49 and the display circuits are shown in Figure 50.
<br>
<br>
<img src="Document/Images/49a Master circuit with soldering parts.png" width="700" >
<img src="Document/Images/49b Master circuit with soldering parts.png" width="700" >
###### Figure 49: Master circuit with soldering parts
<br>

<br>
<img src="Document/Images/50a Display circuit with soldering parts.png" width="700" >
<img src="Document/Images/50b Display circuit with soldering parts.png" width="700" >
###### Figure 50: Display circuit with soldering parts
<br>

### 3.4	 GUI-related results
GUI upgrades were made after the design of the PCB, which allowed for improvements to the GUI and the overall system, and it was helpful to find the system error during the running. In the first case, the GUI was programmed to send data to the system ad tested it, which gave successful results. At that time, the GUI was also developed to change the colour of the buttons on the GUI. GUI during change mode is shown in Figure 51.
<br>
<br>
<img src="Document/Images/51 GUI during change mode.png" width="700" >

###### Figure 51: GUI during change mode
<br>

Then, the system and the GUI were developed to take the data from the master circuit's memory to the GUI. After developing the restarts (Figure 85), the system confirms that the data has been received. This part helps retrieve the memory the GUI needs when the power goes outage and during the system restart. 
<br>
<br>
<img src="Document/Images/52 GUI after the restart.png" width="700" >

###### Figure 52: GUI after the restart
<br>

### 3.5	Reason to upgrade the project
The system had to be modified due to problems with the proposed project and the improvement idea. One of the main ones is the change in communication methods. A centre Triac board for light control was introduced during the proposed project, which required more wire. As a solution, a separate control device control system was introduced. However, the CAT6 cable required is more expensive. Finally, a system was introduced that could be controlled using only a one-pair wire. It can be used for long-distance with two-way communication. It will reduce not only the signal wire but also the power wire.<br>

Another modification of the system is introducing the wireless controlling module to control the device. It works based on the MAC address of the device. It is best to install this home automation system without modifying the existing wiring system.<br>

Next, modification of the system is devolved into the power analysis system. It helps indicates the actual time power flow to the user. The GUI is also designed to show the energy home appliances use. Its other function is introducing overload, high voltage, and current protection.<br>

The other modification is to replace the LCD with a PC-based GUI whether the LCD was used to display data on the system. This new modification also allows the user to display and modify data. It allows the user to modify even the setting data in the system.

