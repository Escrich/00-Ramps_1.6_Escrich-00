## 20251019 Instrucciones para generar y cargar el firmware para RAMPS1.6


https://github.com/Escrich/00-Ramps_1.6_Escrich-00

- Primero hemos de crear el firmware usando KIAUH
Una vez creado, **suponiendo que tu usuario sea biqu**, el firmware quedaría dentro de tu tarjeta de control, 
en este caso una CB1 de BTT, en la siguiente dirección:

**/home/biqu/klipper/out/klipper.elf**

- Ahora tenemos que conectar un programador de chis AVR, en mni caso un Arduino, programado como Arduino as ISP

Asi vemos que está reconociendo el programador de AVR chips:

```
ls -l /dev/serial/by-id/
```

**total 0
lrwxrwxrwx 1 root root 13 Oct 19 14:40 usb-Arduino__www.arduino.cc__0043_952383433343518011A2-if00 -> ../../ttyACM0**

```
ls -l /dev/serial/by-id/
```

ttyACM0

--------------------------------

- Quito el programador, enchufo la placa con el Atmega y repito:

```
ls -l /dev/serial/by-id/
```
**total 0
lrwxrwxrwx 1 root root 13 Oct 19 14:53 usb-FTDI_FT232R_USB_UART_A50285BI-if00-port0 -> ../../ttyUSB0**


/dev/ttyUSB0


Linea para programar el chip Atmega 2560 desde Linux, tras haber generado el archivo de configuración con Kiauh:

```
avrdude -p atmega2560 -c arduino -P /dev/ttyACM0 -b 19200 -U flash:w:/home/biqu/klipper/out/klipper.elf
```

Una vez hecho esto, ya tienes en tu Arduino Mega, la configuración de Klipper necessaria para hacer funcionar una tarjeta de control de impresora del tipo RAMPS 1.6

- Por tanto tu definición del canal USB, que va a comunicar con la tarjeta Arduino Mega, debería ser muy similar a esto:

```
# **********************************************************************************
# Comunicación serie
# **********************************************************************************

[mcu]  # Conexión para BTT-Pi o BTT CB1, no hay diferencia entre ambas
# Placa Ramps Atmega 2560, Puedes usar cualquiera de las dos lineas a continuación pero solo una de ellas o la otra, nunca ambas
#serial: /dev/serial/by-id/usb-FTDI_FT232R_USB_UART_A50285BI-if00-port0
serial: /dev/ttyUSB0
restart_method: command
```

- Ahora, usando el printer.cfg que vas a encontrar en este repositorio, y las dos carpetas con otros complementos, como leds, beeper, servos, etc., tendrás toda la información y toda la configuración, para hacer una impresora Klipper basada en tu tarjeta Ramps 1.6.

- Si por el contrario quieres usarla en Marlin, tambien tienes todos los nombres de pin necesarios para poderla utilizar en Marlin

  **J.M. Escrich 20251020**
