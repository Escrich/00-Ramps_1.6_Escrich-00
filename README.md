# 00-Ramps_1.6_Escrich-00

<br>
<p align="left">
<img src="https://github.com/Escrich/00-Ramps_1.6_Escrich-00/blob/main/Imagenes/Ramps_1.6_0010.jpg" alt='RAMPS 1.6 Escrich' width='70%'>
</p>
<br>

## **Versión Klipper actualizada para impresora con tarjeta Ramps 1.6**

- El inicio de este proyecto está, en que no encontraba ningun sitio donde estuviese toda la información necesaria para poder poner en marcha una tarjeta RAMPS 1.6, siempre tenía que estar buscando por diferentes sitios, diferentes webs, para ir encontrando los trozos del puzzle, al mas puro estilo Indiana Jones, para poder finalmente, hacer algo funcional con ella, además, muchas veces, he encontrado información contradictoria, y otras muchas erronea, incluso en sitios con cierto prestigio, lo que me ha llevado a hacer este repositorio, que lejos de ser un sitio teórico mas, muestra y contiene, un sistema basado en en Arduino Mega, Ramps 1.6 y una tarjeta de control BTT CB1, (esta última puede ser una Raspbery o cualquier tarjeta de control que quieras usar), y que está funcionando con la versión mas actual de Klipper.

- Ya puestos, he añadido al proyecto los sensores y dispositivos mas habituales actualmente, en una maquina con Klipper, estos son:
1. Ventilador de capa
2. Ventilador de hotend, no existe en principio, se usa a partir del conector AUX-2 junto con el Beeper y la tira led, se necesitan mosfets externos para los tres dispositivos
3. Cama caliente
4. Boquilla, (nozzle)
5. 5 Motores, he incluido stepper_z1, en lugar de extruder1, para poner doble z
6. BlTouch
7. Superpinda
8. Salida para servos, e información sobre las direcciones de las cuatro salidas, una usada para Neopixel y otra para BlTouch
9. Salida Neopixel
10. Salida para tira led
11. Información sobre las tres entradas de termistor
12. Información sobre los 6 pins de final de carrera
13. Beeper
14. Sensor de falta de filamento
15. Sensor de movimiento de filamento, Smart sensor
16. Configuración para display, mas util en Marlin que en Klipper

    Además se incluye instrucciones de forzado manual de motores, movimiento de servos, etc, así como completa información acerca de las entrads y salidas utilizadas.
