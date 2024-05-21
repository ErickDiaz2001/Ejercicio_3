INTRODUCCIÓN

Este informe describe un sistema de control que utiliza máquinas de estados con debounce para dos teclas. 
El sistema envía información sobre el estado de las teclas a través de la UART y enciende un LED correspondiente cuando se presiona una tecla.

CONFIGURACION

El system clock del microcontrolador se configuro a 72Mhz.

Se utilizara el timer 2, para obtener una interrupción cada 1 milisegundo se configuro un prescaler a 7200-1 y el counter period a 10. Ademas de habilitar la interrupcion. 
Para la comunicaion se utilizo el usart_3, sin habilitar la interrupcion.

![image](https://github.com/ErickDiaz2001/Ejercicio_3/assets/169405943/cd9eade3-dc9e-49f4-9afd-71f11d27777c)


MÁQUINAS DE ESTADOS CON DEBOUNCE

![image](https://github.com/ErickDiaz2001/Ejercicio_3/assets/169405943/3a176be8-8ce6-40e2-9a39-4e7ec34c782a)

Para evitar el rebote de las teclas, se utilizan máquinas de estados con debounce. Cada tecla tiene su propia máquina de estado, que consta de los siguientes estados:

•	Tecla Inactiva

•	Tecla Presionada

•	Tecla Liberada

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

ANÁLISIS DE RESULTADOS 


CONCLUSIÓN

El sistema de control descrito en este informe utiliza máquinas de estados con debounce para dos teclas de manera efectiva. Esto permite detectar de manera precisa la presión y liberación de las teclas, incluso en presencia de rebote. El sistema también envía información sobre el estado de las teclas a través de la UART y enciende un LED correspondiente cuando se presiona una tecla.
