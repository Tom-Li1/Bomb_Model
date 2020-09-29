# FoolsTimeBomb_micropython

## Micropython based C4 time bomb modle (Under construction)

> A time bomb model with an OLED and 4-number screen and a beeper, which can only be used for a prank (can't explode...)

## Instructions

### Wiring

* TM1637
	* CLK - GPIO16
	* DIO - GPIO5<br>

* Beeper
	* I/O - GPIO4

* SSD1306(I2C)
	* SCL - GPIO0
	* SDA - GPIO2

### Files

* **mian.py**
This script is the main body of the project, upload it to the board and run it according to the startup instructions.

* **create_pixels_list.py**
This script is used to generate a python list based on the pixels of a image file of ppm format, in which the two-dimensional coordinates of each pixel are stored. After the generation, the JSON file which called *image_lattice.json* is created and the list is written to it.
> The contents and names of pictures in ppm format can be changed at will.<br>Please refer to the notes of this script for details

* **image_lattice.json**
Created by the script above, stores the python list from *create_pixels_list.py*. It will be read when *main.py* is running, and the coordinate value of each pixel stored in the list will be displayed on the OLED screen, which means that you need to upload it to the board and place it in the same directory of *main.py*.

### Startup

1. Connect the equipments according to the wiring instructions, and you can solve the power supply mode by yourself.

2. When the board is powered on, the four digit display and OLED screen will all light up, and the buzzer will sound three times. After that, screens will all go out and the OLED screen will display *Ready...* and *WAITING*, and the buzzer will sound once. It means you can proceed to the next step.

3. After that, the board will set up an access point with name 'C4_Bomb' and password '100299301bc'.Connect the access point with phone or PC, the board only accept one device.
> The name and password here are the default content, but you can change it to what you expect in the source code. Find more details in main.py

4. *http://192.168.4.1:24680/5*
Open this URL with a browser after connect to the access point. Then the board will start a 5-minute count down.
> 192.168.4.1 and 24680 is the IP and default port of the board's access point as an example, you can change the port via source code, too.<br>There is a '5' in the end of the URL, this represents the number of minutes to count down, it means that you can change the minute by change the number. **(only accept integers between 1-99)**<br>The IP address may be dynamic and its value is displayed on the OLED screen after each boot. Here is an example, **you should modify the IP address in the link according to what is displayed**.

5. Wait and guess what will happen in the end of count down.