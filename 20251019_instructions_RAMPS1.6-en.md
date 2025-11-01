## 20251020 Instructions to generate and upload the firmware for RAMPS 1.6

<br>
<p align="left">
<img src="https://github.com/Escrich/00-Ramps_1.6_Escrich-00/blob/main/Imagenes/Ramps_1.6_0026.jpg" alt='Programmer Arduino as ISP' width='90%'>
</p>
<br>

- First we must create the firmware using KIAUH.
Once created, assuming your user is "biqu", the firmware will be inside your control board user's home, in this case a BTT CB1, at the following path:

**/home/biqu/klipper/out/klipper.elf**

<br>
<p align="center">
<img src="https://github.com/Escrich/00-Ramps_1.6_Escrich-00/blob/main/Imagenes/Ramps_1.6_0024.PNG" alt='firmware' width='70%'>
</p>
<br>

- This is how we should select options in Kiauh
<br>
<p align="center">
<img src="https://github.com/Escrich/00-Ramps_1.6_Escrich-00/blob/main/Imagenes/Ramps_1.6_0027.png" alt='Kiauh' width='70%'>
</p>

- And these are the chip characteristics, always within Kiauh. Once done, by pressing the Q key it will ask if we want to save our settings, and will start the compilation process.

<br>
<p align="center">
<img src="https://github.com/Escrich/00-Ramps_1.6_Escrich-00/blob/main/Imagenes/Ramps_1.6_0023.PNG" alt='settings' width='70%'>
</p>
<br>

- Now we have to connect an AVR chip programmer; in my case an Arduino programmed as Arduino as ISP.

We can see that the AVR programmer is recognized with:

```
ls -l /dev/serial/by-id/
```

Example output:

```
total 0
lrwxrwxrwx 1 root root 13 Oct 19 14:40 usb-Arduino__www.arduino.cc__0043_952383433343518011A2-if00 -> ../../ttyACM0
```

Then:

```
ls -l /dev/serial/by-id/
```

Which shows:

ttyACM0

--------------------------------

- I remove the programmer, plug in the board with the Atmega and repeat:

```
ls -l /dev/serial/by-id/
```

Example output:

```
total 0
lrwxrwxrwx 1 root root 13 Oct 19 14:53 usb-FTDI_FT232R_USB_UART_A50285BI-if00-port0 -> ../../ttyUSB0
```

/dev/ttyUSB0


Line to program the Atmega2560 chip from Linux, after generating the configuration file with Kiauh:

```
avrdude -p atmega2560 -c arduino -P /dev/ttyACM0 -b 19200 -U flash:w:/home/biqu/klipper/out/klipper.elf
```

<br>
<p align="center">
<img src="https://github.com/Escrich/00-Ramps_1.6_Escrich-00/blob/main/Imagenes/Ramps_1.6_0025.PNG" alt='firmware uploading' width='80%'>
</p>
<br>

- Once this is done, your Arduino Mega will have the Klipper configuration necessary to run a printer controller board of the RAMPS 1.6 type.

- Therefore your USB device definition, which will communicate with the Arduino Mega board, should look similar to this:

```
# **********************************************************************************
# Serial communication
# **********************************************************************************

[mcu]  # Connection for BTT-Pi or BTT CB1, there is no difference between them
# RAMPS Atmega2560 board. You can use either of the two lines below but only one of them, never both
#serial: /dev/serial/by-id/usb-FTDI_FT232R_USB_UART_A50285BI-if00-port0
serial: /dev/ttyUSB0
restart_method: command
```

- Now, using the printer.cfg you will find in this repository, and the two folders with other add-ons such as LEDs, beeper, servos, etc., you will have all the information and configuration needed.

- If, on the other hand, you want to use it in Marlin, you also have all the pin names necessary to use it in Marlin.

**J.M. Escrich 20251020**