2025-08-15 13:21

**Tags:**  #machine_learning #AI  #aprendizajeSupervisado #Regresión_lineal #Regresión_logística #función/hipótesis  #Overfitting #Underfitting

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

Continuando con la metodología para tratar esos datos desde que generamos ese conjunto de datos hasta que se los proporcionamos al algoritmo de #machine_learning, en esta sección veremos uno de los **problemas que surgen con mayor frecuencia cuando tratamos de aplicar técnicas de aprendiza automático a problemas reales**.

>Su nombre es el #Overfitting o #Sobre-entrenamiento. 
>Una de las formas más comunes para poder detectar este problema de #Overfitting es mediante la **división de nuestro conjunto de datos inicial** en diferentes subconjuntos que utilizaremos para diferentes tareas

- Utilizaremos un **subconjunto para entrenar** el algoritmo
- Otro para **validar** que un modelo funciona correctamente
- Otro para **probar que nuestro algoritmo y nuestro modelo generalizan bien para nuevos** ejemplos

#Overfitting 
Si el conjunto de datos tiene muchas características de entrada, es posible que nuestra #función/hipótesis generada por el algoritmo se adapte muy bien al conjunto de entrenamiento (es decir, minimice el error hasta que ese error sea igual a 0) pero falle al generalizar para nuevos ejemplos

Es un problema que ocurre cuando nuestra #función/hipótesis o **nuestro modelo, se adapta perfectamente a los ejemplos de nuestro conjunto de datos de entrenamiento** de nuestro conjunto de datos de experiencia pasada, pero cuando lo ponemos en producción y recibimos nuevos ejemplos, extraemos esas características de entrada y las evaluamos, nuestro algoritmo no se comporta bien.

>Esto es lo que se conoce como #Overfitting: una adaptación muy buena al conjunto de datos de experiencia pasada (conjunto de datos de entrenamiento) pero que no generaliza bien, es decir, no es capaz de realizar buenas predicciones para ejemplos que no ha visto nunca (ejemplos nuevos), o sea esos que no se encuentran en ese conjunto de datos inicial de experiencia pasada

Crear límites de decisión flexibles permite que se adapte de manera perfecta a mi conjunto de datos. Pero se adapta tan bien a los datos de experiencia pasada, que ha generado un límite de decisión muy flexible que no es capaz de predecir correctamente para ejemplos nuevos que le llegan y por lo tanto, aunque el error de nuestro conjunto de datos de entrenamiento es 0 (xq efectivamente se ha adaptado muy bien a esos ejemplos pasados), cuando calculamos el error de ejemplos nuevos, la predicción que nos da nuestro modelo, es una predicción que se encuentra bastante alejada de lo que debería darnos si tenemos en cuenta la tendencia de nuestros datos.

Ver explicación video clase

#Underfitting
Por ejemplo en casos que usemos un modelo de regresión lineal (una recta) cuando no sea apropiado de acuerdo a mi tendencia de datos, ya que la regresión lineal es un modelo muy rígido, sólo podemos construir una recta y si la tendencia de nuestro conjunto de datos no es recta sino que es un poco curva, por lo que el error que tengamos a la hora de predecir datos futuros será grande.

#### Soluciones al overfitting

Una de las formas más comunes para evitar que se produzca #Overfitting o sobre entrenamiento:

- **Aumentar el conjunto de datos:** cuanto más datos de entrenamiento recopilemos y más representativo de los datos que luego nos vayan a llegar, menos sobre entrenamiento se va a producir, porque aumentamos las probabilidades de que haya un dato que tengamos que se parezca a un dato nuevo que llegue luego, así hacemos que el conjunto de datos de entrenamiento sea parecido al conjunto de datos reales que lleguen en el futuro.

- **Reducción del número de características**: porque cuanto más características de entrada tengamos (agregamos más características polinómicas al modelo) más flexible se hace el modelo y tenemos más posibilidad de producir #Overfitting 
Podemos hacerlo de diferentes maneras:
 **1**. Seleccionar de manera manual las características que quiero que se mantengan.
 **2**. Podemos usar un **algoritmo** para que me realice esa selección de características y me diga cuáles son las más importantes y cuáles podemos eliminar porque producirán sobre entrenamiento. 
Ej: #Random_Forest nos permite hacer esta selección de características DE MANERA AUTOMÁTICA
 **3.** Utilizar un conjunto de algoritmos que sirven para la extracción de características.

-  **Regularización:** regulariza aquellas características de entrada que están produciendo sobre entrenamiento

#### Solución al #Overfitting : Regularización 
min 5.50
La regularización va a agregar una penalización a los diferentes parámetros theta0, theta1, thetaN del modelo, con el objetivo de reducir su libertad.











