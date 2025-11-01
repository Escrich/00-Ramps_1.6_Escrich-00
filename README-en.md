# Ramps 1.6 running Klipper by Escrich

<br>
<p align="left">
<img src="https://github.com/Escrich/00-Ramps_1.6_Escrich-00/blob/main/Imagenes/Ramps_1.6_0010.jpg" alt='RAMPS 1.6 Escrich' width='70%'>
</p>
<br>

## Updated Klipper version for printers with a Ramps 1.6 board

- The beginning of this project is that I couldn't find a single place with all the information needed to get a RAMPS 1.6 board running; I always had to search in several places. I decided to gather the information I found and also add what I discovered while testing.

- Additionally, I have included the most common sensors and devices currently used in a Klipper-based machine. These are:
1. Part cooling fan
2. Hotend fan — this is not present by default; it is used from the AUX-2 connector together with the beeper and the LED strip. External MOSFETs are required for these three devices.
3. Heated bed
4. Nozzle (hotend)
5. 5 Motors — I included stepper_z1 instead of extruder1 to allow dual Z.
6. BLTouch
7. Superpinda
8. Servo output, and information about the directions of the four outputs; one is used for Neopixel and another for BLTouch.
9. Neopixel output
10. LED strip output
11. Information about the three thermistor inputs
12. Information about the six endstop pins
13. Beeper
14. Filament runout sensor
15. Filament motion sensor (Smart sensor)
16. Configuration for a display — more useful in Marlin than in Klipper

- The repository also includes instructions for manual motor forcing, servo movement, etc., as well as complete information about the inputs and outputs used.

> TIP:
> Remember that if you do not put the jumper on connector J5, you will not have power for the servos. The usual configuration is to bridge between 5V and VCC, i.e., leave the pin closest to the edge free and short the two inner pins.

<br>

> TIP:
> With this information and the same firmware configuration, not only the firmware but also all the input/output mapping, you can build a printer based on this board... (the original sentence indicates you can use it as a base for other machines).

<br>

> WARNING:
> Pay attention to supply voltages, especially if you are used to printers powered at 24 Volts, which is more common today.
> REMEMBER that the RAMPS 1.6 board is powered at 12 Volts, not 24. If you apply 24 volts you will fry it, and probably the Arduino Mega as well.

<br>

> IMPORTANT:
> As shown in the project, there are no macros like start_print or end_print because those macros depend entirely on what you want to do with your machine. I have not included macros referring to those actions.
>
> Related repositories by the author:
> https://github.com/Escrich/00-Cuore-00
> https://github.com/Escrich/00-Phoenix-X86-00
> https://github.com/Escrich/00-Acqua-00

<br><br>

- This is a work I made hoping it will help others, collecting and showing all the information I managed to find or generate since I started working on this project.

<br>

www.github.com/escrich

https://t.me/escrich

https://www.tiktok.com/@josemescrich

https://www.youtube.com/@josem.escrich2610

<sub>
20251020 Jose M. Escrich
</sub>