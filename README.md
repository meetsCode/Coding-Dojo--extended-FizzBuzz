Intento implementar el algoritmo propuesto en:
http://agilekatas.co.uk/katas/FizzBuzz-Kata
https://gist.github.com/sdecandelario/11d4f53c14efa3a2c753e39c59a3d7a5


en la kata:
https://www.meetup.com/es-ES/Barcelona-Software-Craftsmanship/events/237030117/
del 13 de Febrero de 2017

Lo implementaré en Smalltalk. Usaré Pharo5.0. Sobre cómo usar Pharo lee: https://github.com/meetsCode/Introduccion-PharoSmalltalk 
 
#INTENCIÓN:
La intención del ejercicio es implementar una versión básica de un típico juego de niños, el “Fizz Buzz”. Este juego sirve para repasar las tablas de multiplicar -en su versión más básica- y agilizar el cálculo mental en su versión más compleja.

Cada versión del software muestra la refactorización del código y/o su ampliación para los nuevos requisitos del cliente.

#EL JUEGO:
Es un juego de cartas. Se muestra carta con un número. El primer niño que detecte qué divisores tiene ese número se lleva la carta. Imagino que gana el que más cartas tenga. Cuando el divisor detectado es 3 el niño debe decir la palabra “fizz” si es 5 “buzz” y si es 3 y 5 la frase “fizz buzz”

 

# Respecto a los paquetes que veréis a continuación.
##Primera versión.
Es el código que se escribió al final de la kata. La intención de este código es- desde el principio- evitar la cadena if-then-else y escribir el código POO mejor posible. Para ello aprovechamos el sistema de herencia y el acceso a las subclases que ofrece Smalltalk.

##Segunda versión.En esta segunda versión amplío la cantidad de divisores analizados para cubrir la Feature 2. 
Para ampliar el programa con un divisor de 7 bastó con copiar una clase FBCalculatorX y modificar la respuesta al mensaje #myNumber y el retorno de #divide:Eso lo hice ya en el coding-dojo delante de los compañeros así que para dejar lista esta segunda versión solo tuve que añadir más test. El resto del trabajo ya lo hacía la estructura creada.Alguien comentó una pequeña mejora pendiente: ¿Qué sucede si quiero modificar el método que hace el cálculo porque ya no me interesa que sea el divisor sino otra propiedad? En ese caso-tal y como aparece ahora- tendría que ir modificando una a una todas las subclases de FizzCalculator. Él tenía razón, eso es muy engorroso. La solución para la siguiente versión. 

##Tercera versión
En esta versión 3 intento mejorar el código sin llegar a implementar el "Feature 3".Ya lo comenté antes: Conforme aparecen divisores la lista de subclases de FizzCalculator se amplía. Eso no es malo pero si en algún momento se considera que el cálculo a realizar cambie tendré que ir clase a clase cambiando el mensaje #divide:La solución a esto es pasar el mensaje #divide: a la superclase. Para ello además debo de dar como variable la cadena de texto-resultado.


##Cuarta versión
Otro asunto menor pero molesto era el tema de los espacios entre los mensajes y el orden de estos.Pongo un ejemplo. En el caso de  105 la clase FizzCalculator respondia 'popbuzzfizz' en lugar de 'fizz buzz pop'.Con esta versión queda corregido el asunto. Lo he hecho pidiendo a las subclases que se ordenen por su #myNumber antes de consultarlas.
El test debió cambiar para aceptar las nuevas soluciones





