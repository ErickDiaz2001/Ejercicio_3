INTRODUCCIÓN

Este informe describe un sistema de control que utiliza máquinas de estados con debounce para dos teclas. 
El sistema envía información sobre el estado de las teclas a través de la UART y enciende un LED correspondiente cuando se presiona una tecla.

MÁQUINAS DE ESTADOS CON DEBOUNCE

![image](https://github.com/ErickDiaz2001/Ejercicio_3/assets/169405943/0af4d7b5-b2cb-4b67-9db0-039430eed827)

Para evitar el rebote de las teclas, se utilizan máquinas de estados con debounce. Cada tecla tiene su propia máquina de estado, que consta de los siguientes estados:

•	Tecla Inactiva: La tecla está en estado bajo, hasta que sea confirmado la pulsación.

•	Tecla Presionada: La tecla se ha presionado, se ha confirmado la pulsación.

•	Tecla Liberada: La tecla se ha confirmado como liberada.

Las máquinas de estado realizan las siguientes transiciones:

•	Tecla Inactiva a Tecla Presionada: Cuando se detecta un pulso de la tecla.

•	Tecla Presionada: Inicia de un tiempo de debounce (10 ms).

•	Tecla Presionada a Tecla Liberada: Después de un tiempo de debounce.

•	Tecla Inactiva: Cuando se detecta un pulso bajo de la tecla.

ENVÍO DE INFORMACIÓN POR UART

Cada vez que una tecla se presiona o se suelta, el microcontrolador envía un mensaje a través de la UART. El mensaje contiene el identificador de la tecla (tecla 1 o tecla 2) 

y el nuevo estado de la tecla (presionada o liberada).

ENCENDIDO DE LEDS

Cuando se presiona una tecla, el LED correspondiente se enciende. El LED permanece encendido hasta que se suelta la tecla.
