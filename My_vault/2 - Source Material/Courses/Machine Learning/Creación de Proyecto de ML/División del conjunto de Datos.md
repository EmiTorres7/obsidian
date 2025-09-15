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
**Índice**
[[#Soluciones al overfitting]]
[[#Solución al Overfitting Regularización]]
[[#Evaluación de la hipótesis]]

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

-  **Regularización:** regulariza aquellas características de entrada que están produciendo sobre entrenamiento. Básicamente lo que hace es añadir una penalización a determinados parámetros de mi modelo de manera que se reduzca la flexibilidad de mi modelo.
La regularización va a reducir esos parámetros que están produciendo sobre entrenamiento, de manera que se regule un poco la flexibilidad del modelo y no se ajuste tanto a nuestro conjunto de datos de entrenamiento (o sea que no sea tan rígido).

#### Solución al #Overfitting : Regularización 

La regularización va a agregar una penalización a los diferentes parámetros theta0, theta1, thetaN del modelo, con el objetivo de reducir su libertad.

Así logramos hacer menos probable que nuestro modelo se ajuste demasiado bien a nuestros datos de entrenamiento y así será más probable que mejore sus capacidades para generalizar correctamente para nuevos ejemplos que no haya visto nunca.

Va a mantener todas las características de entrada, es decir que no va a eliminar características o atributos de entrada, pero va a reducir la magnitud de los parámetros del modelo (theta0, theta1, theta n). Va a tratar de reducir el valor de los parámetros  para que se ajusten un poquito peor a nuestro conjunto de datos de entrenamiento y así esto provoque que generalice mejor para ejemplos nuevos que nuestro modelo no haya visto antes.

La regularización funciona muy bien cuando tenemos muchas características de entrada

Si tenemos el ejemplo de:
eje x: número de equipos afectados
eje y: costo

Si usamos un modelo muy flexible ( #función/hipótesis) se puede producir #Overfitting o #Sobre-entrenamiento de manera que nuestro modelo se adaptaba muy bien a nuestros ejemplos de nuestro conjunto de datos donde el error resultante será 0 porque nuestro modelo predice demasiado bien.
Si bien se ajusta perfectamente a nuestro conjunto de datos de entrenamiento, al colocar un nuevo ejemplo que mi modelo no haya visto antes (no estaba en mi conjunto de datos de entrenamiento).

>Para solucionar el #Overfitting, una de las maneras es mediante la **Regularización**
>
>Lo que hace es penalizar los parámetros de mi modelo (theta0, theta1, thetaN), lo que hace es que en lugar de tener únicamente esta #funcion_deCoste_error en el que ya he encontrado unos parámetros theta0, theta1, thetaN óptimos que minimizan el error pero que forman una #función/hipótesis que no generaliza correctamente... 
>
>Lo que hacemos es añadirle un término más, que es un término de regularización que lo que hará es añadir una penalización sobre esa #funcion_deCoste_error de manera que, aunque sea el valor óptimo para el conjunto de datos, tenga que seguir minimizando esos parámetros de manera que generemos un poquito más de error para los ejemplos de nuestro conjunto de datos de entrenamiento, pero sea capaz de predecir bien para nuevos errores

>Entonces le va añadir un término de penalización que viene dado por lambda que es una constante que básicamente va a decidir cuánto queremos reducir la flexibilidad de nuestro modelo, es decir, cuánta penalización queremos añadir

>Mediante este parámetro lambda lo que haremos será controlar la flexibilidad o la rigidez de ese modelo

## Evaluación de la hipótesis
[[#Overfitting y Underfitting]]
[[#Solución al Overfitting Regularización]]

**Tags:** #Train_Set y #Test_Set 

**¿Cómo podemos evaluar que para un conjunto de datos en el que tenemos un número muy elevado de características que pueden estar provocando #Overfitting? **

¿Cómo podemos evaluarlo de manera práctica para saber si se está produciendo o no #Overfitting y, en el caso que se esté produciendo, tomar las medidas que hemos visto anteriormente? como reducir características, aplicar regularización, aumentar el conjunto de datos, etcétera.

- Para ello, vamos a dividir nuestro conjunto de datos en diferentes subconjuntos y utilizar cada uno de ellos para una tarea específica

-Para entrenar nuestro algoritmo utilizaremos un subconjunto
-Para evaluar que nuestro algoritmo se comporta correctamente, utilizaremos otros conjuntos

conjunto de datos de entrenamiento -> paso los datos y me construye una #función/hipótesis 


**¿Cómo sé que mi #función/hipótesis que he construido me está produciendo #Overfitting ?**
Para esto vamos a dividir nuestro conjunto de datos de entrenamiento en 2 subconjuntos:

1. Subconjunto de entrenamiento: #Train_Set 60-70%
2. Subconjunto de pruebas: #Test_Set 40-30%

El #Train_Set estará en torno al 60-70% y el #Test_Set estará en torno al 40-30% de todos nuestros datos iniciales que tenemos en ese conjunto de datos de experiencia pasada que hemos recopilado para un problema en concreto.

Vamos a utilizar el primer subconjunto que se corresponde únicamente con los datos de experiencia pasada... primero el #Train_Set , o sea usamos el 60 o 70% de esos datos para entrenar primero mi algoritmo y generar mi modelo #función/hipótesis ajustada, que producirá desde luego #Overfitting sobre mi conjunto de datos.

Pero luego, no voy a usar ese mismo subconjunto de datos para realizar las predicciones y ver qué tal se comporta, sino que voy a utilizar el 2do subconjunto de pruebas, el resto del 30% o 40% que correspondería a mi #Test_Set 
Aquí en este 2do subconjunto lo que haré es eliminar o apartar la etiqueta "Y" y me voy a quedar únicamente con las características de entrada "X", entonces tomamos esa característica de entrada X y la vamos a evaluar sobre la #función/hipótesis que habíamos generado con el #Train_Set 

>Así esos ejemplos o características X del #Test_Set nunca fueron vistas por nuestro algoritmo, porque esta #función/hipótesis fue generada con los datos de #Train_Set, entonces los toma como nuevos ejemplos.
>Una vez que he calculado una predicción para cada uno de ellos, comparamos esas prediccciones con las que generó con los ejemplos del otro subconojunto.

**Resumen:**
>Genero una #función/hipótesis con los datos del subconjunto de datos del #Train_Set y para comprobar si este modelo o #función/hipótesis está produciendo #Overfitting sobre este subconjunto, le pasaremos ejemplos que no ha visto nunca, que serían los datos restantes, ese 30 o 40% correspondiente al subconjunto del #Test_Set 
>Una vez que me ha realizado las predicciones para estos ejemplos, vamos a comparar las predicciones con la etiqueta que tienen en mi conjunto de datos.

>Lo vamos a ver cuando el error que se genera para los valores que no ha visto nunca, es decir para el #Test_Set , sea muy grande, mientras que el error para el #Train_Set será 0 obviamente. 
>
>Se adapta muy bien para el conjunto de datos de entrenamiento pero no para los nuevos ejemplos que no ha visto nunca, por eso para el #Test_Set dará un error grande si es que se está produciendo #Overfitting 

---
## Selección de un modelo
Video: Sección 7: Creación de un proyecto de Machine Learning - 47. Selección del Modelo

>- Si el error en el #Train_Set es pequeño pero en el #Test_Set es grande -> #Overfitting 
> 
>- Si el error en el #Train_Set es grande y en el #Test_Set es grande -> no es el modelo adecuado, tengo que añadir más características polinómicas porque no tiene la suficiente flexibilidad para adaptarse a la tendencia de mi conjunto de datos, por lo cual tendría que seguir evaluando más modelos, un modelo 2 y hacemos lo mismo, calculamos #funcion_deCoste_error para mis datos de entrenamiento #Train_Set y luego lo evalúo para mi conjunto de datos de prueba #Test_Set y con los ejemplos que no ha visto anteriormente calculo el error para mi #Test_Set 

>Probablemente tengamos que hacer esto varias veces hasta por ejemplo tener 5 características de entrada y obtener otro modelo y de nuevo lo mismo, calcular #funcion_deCoste_error para el #Train_Set y para el #Test_Set 

 - Si el error en el #Train_Set es pequeño pero en el #Test_Set es grande -> #Overfitting 
 
 - Si el error en el #Train_Set es grande y en el #Test_Set es grande -> no es el modelo adecuado

- Si el error en el #Train_Set es bajo y en el #Test_Set también es bajo -> el modelo en concreto se está comportando adecuadamente 

	Para seleccionar un modelo adecuado es necesario dividir el conjunto de datos en 3:
	- datos de entrenamiento #Test_Set 
	- datos de prueba #Test_Set 
	- datos de validación #Validation_set


**Selección de un modelo - Pasos**

1. Dividimos el conjunto de datos en entrenamiento, validación y pruebas

2. Se calcula la #función/hipótesis con el subconjunto de entrenamiento #Train_Set (se calculan los parámetros theta minimizando el error de entrenamiento J(theta))

3. Se calcula el número de características óptimo mediante la evaluación de las hipótesis anteriores con el subconjunto de validación #Validation_set 

4. Se evalúa la #función/hipótesis resultante mediante el subconjunto de pruebas #Test_Set  calculando su error.

(Ver video)




