https://github.com/Escrich/00-Ramps_1.6_Escrich-00

Primero hemos de crear el firmware usando KIAUH
Una vez creado, suponinedo que tu usuario sea biqu, el firmware quedaría dentro de tu tarjeta de control, 
en este caso una CB1 de BTT, en la siguiente dirección:

/home/biqu/klipper/out/klipper.elf


Asi vemos que está reconociendo el programador de AVR chips:
biqu@CB1:~$ ls -l /dev/serial/by-id/
total 0
lrwxrwxrwx 1 root root 13 Oct 19 14:40 usb-Arduino__www.arduino.cc__0043_952383433343518011A2-if00 -> ../../ttyACM0

ls -l /dev/serial/by-id/

ttyACM0

--------------------------------

Quito el programador, enchufo la placa con el Atmega y repito:
biqu@CB1:~$ ls -l /dev/serial/by-id/
total 0
lrwxrwxrwx 1 root root 13 Oct 19 14:53 usb-FTDI_FT232R_USB_UART_A50285BI-if00-port0 -> ../../ttyUSB0


/dev/ttyUSB0


Linea para programar el chip Atmega 2560 desde Linux, tras haber generado el archivo de configuración con Kiauh:

avrdude -p atmega2560 -c arduino -P /dev/ttyACM0 -b 19200 -U flash:w:/home/biqu/klipper/out/klipper.elf

Una vez hecho esto, ya tienes en tu Arduino Mega, la configuración de Klipper necessaria para hacer funcionar una tarjeta de control de impresora del tipo RAMPS 1.6