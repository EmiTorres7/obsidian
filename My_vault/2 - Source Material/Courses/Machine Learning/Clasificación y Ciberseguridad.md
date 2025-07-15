2025-07-14 16:10

**Tags:** #machine_learning #aprendizajeSupervisado  #Regresión_logística #regresión #Regresión_lineal #algoritmo_clasificación #threshold #función/hipótesis  #Función_sigmoide #funcion_deCoste_error #funcion_optimización 

---
###### **References:**
-  **Índice:** [[CURSO MACHINE LEARNING]] 
- [[Qué es Machine Learning]]
- [[Qué es Machine Learning#Sección 5 - Clasificación de los sistemas de Machine Learning]]
- [[Qué es Machine Learning#**Aprendizaje Supervisado** aprendizajeSupervisado]]
---
#### SECCIÓN 6 - CLASIFICACIÓN Y CIBERSEGURIDAD  

Los profesionales que se dedican a la seguridad de la información y ciberseguridad están **constantemente realizando procesos de #clasificación #algoritmo_clasificación**. 

**Por ejemplo:**

- para un correo electrónico, ¿ese correo es phishing, es spam? 

- Para un fichero enviado a través de la red, ¿ese fichero puede que contenga malware (software malicioso que daña o roba información de dispositivos electrónicos), o puede ser una filtración de información? 

- Para una petición hacia el exterior, ¿se corresponde con una llamada a un comand and control C&C?  

>C&C: Es una comunicación entre un atacante y un dispositivo comprometido, a través de una red. Los atacantes utilizan el C2 para controlar los dispositivos comprometidos, propagar malware, robar información, y lanzar nuevos ataques. 

Por eso es importante saber si es una llamada legítima de un usuario a un servidor determinado o si es una llamada de malware que tiene un usuario en un equipo y está haciendo una llamada a un comand and control. 

- Para una petición entrante a nuestra red, ¿se trata de una petición que forma parte de un ataque de denegación de servicio, o que forma parte de un escaneo de servicios o de puertos? 

Todo esto es una pequeña parte de los procesos de #clasificación que diferentes profesionales se dedican en el ámbito de la seguridad de la información. 

Todos estos procesos de #clasificación, no puede hacerlo un analista de manera manual. 

>La forma de realizar estos procesos cuando tenemos millones de eventos, peticiones entrantes, salientes, montones de ficheros que nos intercambiamos, etc, básicamente se realiza a través de la **recolección de datos**. 

>Cuando alguien hace una **petición a un servidor**, se **recolectan los datos**, es decir, se recolectan los logs, cuando alguien manda un determinado fichero se estaría recogiendo ese envío en algún sitio. 

Muchas veces el **problema no viene en la recolección de esa información** porque prácticamente todos tienen implementados diversos procesos con los cuales van a recoger esos logs o información sobre la actividad que se está originando dentro de la infraestructura tecnológica de la compañía. 

Sin embargo, muchas veces o no llega a procesarse esa información nunca o si se procesa, se procesa de manera sencilla.  

Es importante recalcar que no todo el procesamiento que se realiza sobre conjuntos de datos no tiene por qué ser necesariamente #machine_learning.
Por ejemplo, que el analista determine ciertas reglas basándose en hechos del pasado como ataques de fuerza bruta que vienen desde una misma dirección IP, por lo tanto pondrá como regla que si llegan más de 5 o 10 peticiones en un minuto (ataques) se bloquee esa dirección IP, de esta forma no hemos aplicado nada de #machine_learning 

> #machine_learning entra en juego en por ejemplo por qué el analista ha elegido que sean más de 10 peticiones en un minuto y por qué no 5 o en más tiempo, etc, es deicr, qué criterio ha usado para elegir 10 y no 11 o un minuto y no 2 minutos o 3... o qué ocurre si ese ataque en algún momento determinado cambia.

> Las técnicas de #machine_learning y concretamente las técnicas de #clasificación o #algoritmo_clasificación vienen a solucionar este problema

Esto es porque estas técnicas de #machine_learning o aprendizaje automático, consisten principalmente en utilizar algoritmos que van a procesar todo ese histórico de datos y van a inferir reglas de clasificación propias o reglas internas que van a considerarse óptimas no de acuerdo al criterio experto de una persona, sino, de acuerdo a un conjunto de principios matemáticos.

Estos principios matemáticos se van a encargar de inferir las reglas y nosotros no tendremos que analizar todo ese volumen de eventos e ir actualizándolo constantemente.

>En lugar de eso, nosotros vamos a poder pasar ese conjunto grande de datos a un conjunto de algoritmos matemáticos que vana inferir ya las reglas para ser capaces de determinar si un ejemplo nuevo es malicioso o no.
>
>En algunos casos se requerirá que el analista realice un análisis previo de esos nuevos datos clasificándolos como maliciosos o legítimos de manera que se lo proporcionemos al algoritmo, y este sea capaz de aprender una #función/hipótesis ajustada en base a su **modelo** generado, que realice predicciones para todos los datos nuevos que se vayan generando en el futuro.

>En algunos casos, el algoritmo puede ser capaz de detectar anomalías en conjunto de datos sin etiquetar (o sea sin necesidad que previamente el analista haya proporcionado esa categoría **variable Y** de malicioso o legítimo a esos datos que tenemos dentro de nuestro conjunto de datos)








