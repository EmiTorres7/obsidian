2025-07-12 16:31

**Tags:** #machine_learning #aprendizajeSupervisado  #Regresión_logística #regresión 

### SECCIÓN 6 - REGRESIÓN Y CLASIFICACIÓN 

###### **References:**
-  **Índice:** [[CURSO MACHINE LEARNING]] 
- [[Qué es Machine Learning]]
- [[Qué es Machine Learning#Sección 5 - Clasificación de los sistemas de Machine Learning]]
- [[Qué es Machine Learning#**Aprendizaje Supervisado** aprendizajeSupervisado]]
---
#### ALGORITMO DE REGRESIÓN LOGÍSTICA #Regresión_logística  

El algoritmo basado en regresión logística, a diferencia del algoritmo de regresión lineal que veníamos viendo, se va a caracterizar porque va a tratar de predecir un valor discreto por eso a veces se ve referido este tipo de algoritmo como Algoritmo de Clasificación. 

Se caracteriza: 

. Es un algoritmo basado en un aprendizaje supervisado, al igual que el algoritmo de regresión lineal, lo que quiere decir que va a recibir un conjunto de datos etiquetados, este se caracteriza porque tiene los valores de entrada y los valores de salida. 

. Es un algoritmo basado en Aprendizaje basado en modelos, lo que quiere decir que van a construir un modelo o una función/hipótesis (al igual que el algoritmo de regresión lineal). 

. Se va a corresponder también con un modelo lineal, no es un modelo lineal puro sino que es un modelo lineal generalizado. 

Va a construir también una función/hipótesis que también será lineal, al menos cuando lo construyamos con 1 o 2 características, por lo tanto, nos vamos a quedar con que se corresponde con un modelo lineal 

. También van a realizar predicciones computando una suma ponderada de las características de entrada y sumándole una constante conocida como bias (recordar que en el algoritmo de regresión lineal, esta constante bias era el tetha 0 que nombrábamos en la función hipótesis de la regresión lineal), pero aquí habrá una diferencia, y es que al resultado de esa función o de esa suma ponderada se le va a aplicar una función logística y es por ello por lo que recibe el nombre de regresión logística 

. Lo que más diferencia este algoritmo de la regresión lineal es que Intenta predecir valores discretos, mientras que a regresión lineal trataba de predecir valores continuos, es decir, valores que se encontraban dentro de un rango muy amplio de valores como el costo de un determinado incidente de seguridad, en este caso los algoritmos basados en regresión logística van a tratar de predecir valores discretos, es decir valores que se van a encontrar dentro de un rango acotado, como por ejemplo si un correo electrónico es spam o no lo es.