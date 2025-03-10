## 1. Interrupciones

- La mayoría de microcontroladores ofrece una solución para atender algunos tipos de eventos sin ocupar instrucciones en el programa principal
- Tan pronto como ocurre la interrupción el microcontrolador invoca una rutina de servicio de interrupción (interrupt service routine ISR

## 2. Bits IE e IF

>  🔑 IE = (Interrupt enable) habilita el microcontrolador para que detecte ciertos tipos de eventos (llama el ISR)

>  🔑 IF = IF: (Interrupt flag) indica el estado de la interrupción. Si ocurre la interrupción el microcontrolador la configura en 1.

- Dependiendo de la familia de microcontroladores este bit se configura en cero automaticamente o por instrucción del programador

## 2.1 Control de la Interrupción

- En algunas familias de micorocontroldores se puede encontrar que se comparta un bit de IE para gestionar las interrupciones de varias fuentes

## 3. Control de la Interrupción

>  🔑 Modo de interrupción : Estos bits permiten controlar algunas características del evento que provoca la interrupción

>  🔑 Interrupciones globales : Es posible desactivar todas las interrupciones del microcontrolador con la configuración de un solo bit

## 4. Tabla de Vectores de Interrupción

- El mapeo de la interrupción al ISR se almacena en la tabla de vectores de interrupción
- Un vector de interrupción es un número asociado a cada interrupción
- Cuando se ejecuta una interrupción se carga en la memoria de programa una dirección asociada

## 5. Prioridad de Interrupciones 

- Debido a la cantidad de interrupciones, los microcontroladores permiten asignar prioridad a las diferentes llamadas al ISR
- La prioridad permite por ejemplo establecer, si una interrupción puede nterrumpir otra interrupción

## 6. Eventos Externos

- Los microcontroladores detectan cambios de estado (nivel de tensión) en los puertos digitales de entrada por medio de los cambios de flanco de la señal
- El módulo de interrupciones muestrea el Puerto cada ciclo de reloj y lo compara con el estado anterior 
- Debido a que estas interrupciones provienen de hardware externo se pueden ver afectadas por fenómenos como el ruido

## 7. Eventos Internos

- Los microcontroladores también pueden generar interrupciones cada vez que ocurren ciertos evento internamente
- Por tratarse de señales internas este tipo de interrupciones no sufren de problemas como el ruido

## 8. Consideraciones de implementación 
### 8.1 Verificar Puertos/Uso de Interrupciones

| Verificar Puertos                                          | Usar Interrupciones                           |
|------------------------------------------------------------|-----------------------------------------------|
| El operador es un Humano                                   | Los eventos no ocurren periódicamente         |
| No requiere sincronizarse con ningún  evento o dispositivo | Hay intervalos largos de tiempo entre eventos |
| El estado es importante                                    | El cambio de estado es importante             |
| Las señales son ruidosas                                   | Eventos son generados por Hardware            |
|       No hay muchas tareas para ejecutar  en el main       |      Se realizan varias tareas en el main     |

### 8.2 ¿Cual es mejor?

- La desición depende principalmente de la cantidad de tareas que se tengan que ejecutar en el programa principal
- También del problema que se esté solucionando

## 9. Conclusiones
 
- Las interrupciones permiten a los microcontroladores responder a eventos en tiempo real sin la necesidad de estar ejecutando constantemente 
bucles de monitoreo, lo que optimiza el uso de los recursos del sistema.
- Gracias a las interrupciones, los microcontroladores pueden gestionar múltiples eventos de hardware y software de manera eficiente, asignando
prioridades y ejecutando las tareas críticas sin afectar el flujo principal del programa
- Un diseño adecuado de interrupciones evita la sobrecarga del procesador y bloqueos en la ejecución del código principal, asegurando un flujo continuo en la operación del sistema.

