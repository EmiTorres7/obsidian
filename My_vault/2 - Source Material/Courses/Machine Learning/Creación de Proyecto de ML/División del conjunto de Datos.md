2025-08-15 13:21

**Tags:**  #machine_learning #AI  #aprendizajeSupervisado #Regresión_lineal #Regresión_logística #función/hipótesis 

### Creación de un proyecto de Machine Learning 

###### **References:**
**Link:** [Notebook División del Conjunto de Datos](http://localhost:8888/notebooks/7_Divisi%C3%B3n%20del%20conjunto%20de%20datos.ipynb?)
-  **Índice:** [[CURSO MACHINE LEARNING]] 
- [[Qué es Machine Learning]]
- [[Qué es Machine Learning#Sección 5 - Clasificación de los sistemas de Machine Learning]]
- [[Qué es Machine Learning#**Aprendizaje Supervisado** aprendizajeSupervisado]]
---
# Overfitting y Underfitting

Tenemos un conjunto de datos que recopila información de experiencia pasada donde en nuestro caso tenemos que clasificar una transacción como fraudulenta o legítima, por lo que componemos ese conjunto de datos con transacciones pasadas donde hicimos un análisis y las clasificamos como legítimas o fraudulentas. #aprendizajeSupervisado (datos etiquetados)

Le proporcionamos estos datos a un algoritmo de #machine_learning y este con estos datos ajusta una #función/hipótesis, esto consiste básicamente en encontrar el valor de los parámetros theta0, theta1, thetaN que parametrizan este modelo óptimo de manera que minimizábamos esa #funcion_deCoste_error 

Continuando con la metodología para tratar esos datos desde que generamos ese conjunto de datos hasta que se los proporcionamos al algoritmo de #machine_learning, en esta sección veremos uno de los problemas que surgen con mayor frecuencia cuando tratamos de aplicar técnicas de aprendiza automático a problemas reales.

>Su nombre es el #Overfitting o #Sobre-entrenamiento. Una de las formas más comunes para poder detectar este problema de #Overfitting es mediante la **división de nuestro conjunto de datos inicial** en diferentes subconjuntos que utilizaremos para diferentes tareas

- Utilizaremos un subconjunto para entrenar el algoritmo
- Otro para validar que un modelo funciona correctamente
- Otro para probar que nuestro algoritmo y nuestro modelo generalizan bien para nuevos ejemplos

#Overfitting 
Es un problema que ocurre cuando nuestra #función/hipótesis o nuestro modelo, se adapta perfectamente a los ejemplos de nuestro conjunto de datos de entrenamiento de nuestro conjunto de datos de experiencia pasada, pero cuando lo ponemos en producción y recibimos nuevos ejemplos, extraemos esas características de entrada y las evaluamos, nuestro algoritmo no se comporta bien.
Esto es lo que se conoce como #Overfitting: una adaptación muy buena al conjunto de datos de experiencia pasada (conjunto de datos de entrenamiento) pero que no generaliza bien, es decir, no es capaz de realizar buenas predicciones para ejemplos que no ha visto nunca (ejemplos nuevos), o sea esos que no se encuentran en ese conjunto de datos inicial de experiencia pasada

Crear límites de decisión flexibles permite que se adapte de manera perfecta a mi conjunto de datos. Pero se adapta tan bien a los datos de experiencia pasada, que ha generado un límite de decisión muy flexible que no es capaz de predecir correctamente para ejemplos nuevos que le llegan y por lo tanto, aunque el error de nuestro conjunto de datos de entrenamiento es 0 (xq efectivamente se ha adaptado muy bien a esos ejemplos pasados), cuando calculamos el error de ejemplos nuevos, la predicción que nos da nuestro modelo, es una predicción que se encuentra bastante alejada de lo que debería darnos si tenemos en cuenta la tendencia de nuestros datos.

#Underfitting
