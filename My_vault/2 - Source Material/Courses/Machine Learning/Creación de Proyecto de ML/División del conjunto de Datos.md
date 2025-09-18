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
###### **Índice**
- [[#Soluciones al overfitting]]
- [[#Solución al Overfitting Regularización]]
- [[#Evaluación de la hipótesis]]
- [[#Ejercicio División del Conjunto de Datos]]

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

---
#### Soluciones al overfitting
[[#**Índice**]]

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
[[#**Índice**]]

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

---
## Evaluación de la hipótesis
[[#Overfitting y Underfitting]]
[[#Solución al Overfitting Regularización]]
[[#**Índice**]]

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
[[#**Índice**]]

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

---
## Ejercicio División del Conjunto de Datos
[[#Índice**]]

Vemos cómo tenemos que manejar un conjunto de datos para resolver un problema real mediante el uso de #machine_learning , dividiendo ese conjunto de datos en subconjuntos:

- subconjunto de datos de entrenamiento #Train_Set 
- subconjunto de datos de prueba #Test_Set 
- subconjunto de datos de validación #Validation_set 

Cada uno de estos subconjuntos va a tener una función:
- #Train_Set tendrá como función construir o ajustar esa #función/hipótesis de los algoritmos de #machine_learning 

- #Train_Set y #Validation_set tienen como objetivo probar que estos algoritmos o estos modelos ajustados realizan buenas predicciones, ven si no están produciendo #Overfitting, #Underfitting o cualquier otro tipo de problemas similares.

Como vemos en este conjunto de datos NSL-KDD tenemos:
- KDDTrain+.TXT #Train_Set 
- KDDTest+.TXT: #Test_Set 

Este conjunto de datos en concreto ya viene dividido en #Train_Set y #Test_Set 
Entonces aquí ya podríamos cargar por un lado el #Train_Set y por otro lado el #Test_Set y dividir el #Test_Set a su vez en datos de pruebas #Test_Set y datos de validación #Validation_set 

>Ahora veremos cómo podemos utilizar las **funciones de SK-Learn** para partir un conjunto de datos inicial en subconjuntos que vamos a necesitar para entrenar nuestro algoritmo y luego para probarlo 

>Vamos a partir este conjunto de datos de entrenamiento KDDTrain+.TXT #Train_Set aunque ya nos den divido los datos en #Train_Set y #Test_Set, vamos a considerar que el #Train_Set se corresponde con el conjunto de datos total, o sea lo vamos a tratar como el conjunto inicial y lo vamos a partir en un subconjunto de #train_set, uno de #Test_Set y un subconjunto de #Validation_set 

---
##### **1. Lectura del conjunto de datos**
- Lo primero que hacemos como siempre es leer el conjunto de datos
- Importamos el módulo arff y ejecutamos la función load_kdd_dataset()
- Luego cargamos nuestro conjunto de datos con esa función, lo tendremos al único conjunto de datos cargado en df que se corresponde con un data_frame de pandas.
- Visualizamos con df.info()

Data columns (total 42 columns):
 #   Column                       Non-Null Count   Dtype  
---  ------                       --------------   -----  
 0   duration                     125973 non-null  float64
 1   protocol_type                125973 non-null  object 
 2   service                      125973 non-null  object 
 3   flag                         125973 non-null  object 
 4   src_bytes                    125973 non-null  float64
 5   dst_bytes                    125973 non-null  float64

RangeIndex: 125973 entries, 0 to 125972
Data columns (total 42 columns):

Está formado por 125973 ejemplos y 42 columnas incluyendo la variable de salida, es decir, 41 características de entrada X1, X2, X41 y una variable de salida que sería Y.
Como empieza en 0, la variable Y que sería la número 42, en el data_set se corresponde en la posición 41 que sería la clase de esos flujos, es decir si son flujos anómalos o legítimos.

Una vez que tenemos el conjunto de datos inicial, vamos a dividir este conjunto inicial en diferentes sub-conjuntos.
#Train_Set #Test_Set #Validation_set 

>Sklearn tiene implementada la función *split_train_test*.

Esta función divide el conjunto de datos en 2 subconjuntos en base a una proporción que nosotros le pasamos.
```python
#Separamos el conjunto de datos 60% train set, 40% test set
from sklearn.model_selection import train_test_split

train_set, test_set = train_test_split(df, test_size=0.4, random_state=42)
```

1. La importamos a la función split_train_test()
2. le pasamos el data_set que sería el df
3. test_size le paso una proporción de un 40% al #Test_Set 
4. random_state es una semilla 

#Train_Set tiene el 60% de la información
#Test_Set tiene el 40% de los datos del conjunto inicial

>train_set.info()
>Index: 75583 entries, 98320 to 121958  
   Data columns (total 42 columns): 

75583 ejemplos en nuestro #Train_Set 
41 características de entrada X1, X2,...,X41 y 
1 característica de salida Y dada por la clase

 #   Column                       Non-Null Count  Dtype  
---  ------                       --------------  -----  
 0   duration                     75583 non-null  float64
 1   protocol_type                75583 non-null  object 
 2   service                      75583 non-null  object 
 3   flag                         75583 non-null  object 
 4   src_bytes                    75583 non-null  float64
 5   dst_bytes                    75583 non-null  float64

>test_set.info()
>Index: 50390 entries, 378 to 89600
>Data columns (total 42 columns)

50mil ejemplos en nuestro #Test_Set 
41 características de entrada X
1 característica de salida Y

>Para evaluar diferentes modelos que podemos aplicar a un problema necesitamos dividir ese conjunto de datos de prueba, el #Test_Set en otro subconjunto, así tendremos 3 subconjuntos en total.

```r
# Separamos el conjunto de datos de pruebas 50% validation set, 50% test set
val_set, test_set = train_test_split(test_set, test_size=0.5, random_state=42)
```

Usamos la misma función *train_test_split()* pero ahora le proporcionamos el test_set y lo dividiremos en 2 subconjuntos, dejando el 50% a un subconjunto #Test_Set  y un 50% al otro subconjunto #Validation_set 

```python
print("Longitud del Training Set:", len(train_set))
print("Longitud del Validation Set:", len(val_set))
print("Longitud del Test Set:", len(test_set))

Longitud del Training Set: 75583
Longitud del Validation Set: 25195
Longitud del Test Set: 25195
```

> **Este es el método más común utilizado para particionar datos en subconjuntos**

---
#### Particionado aleatorio y Stratified Sampling

Sklearn tiene implementa la función **train_test_split**, sin embargo, esta función por defecto realiza un particionado del conjunto de datos aleatorio para cada vez que se ejecuta el script. 
Aún añadiendo una semilla fija para generación aleatoria como el número 42, cada vez que carguemos de nuevo el conjunto de datos se generarán nuevos subconjuntos. Esto puede ocasionar que después de mucho intentos, el algoritmo "vea" todo el conjunto de datos.

Como hace un partiocionado aleatorio, puede que ya directamente el algoritmo vea todos los datos si nosotros cargamos varias veces de nuevo el jupiter notebook.
Entonces lo que yo tenía en el #Test_Set puede que luego pase al #Train_Set y así, de manera que se estaría produciendo un #Overfitting porque no estaríamos dividiendo de manera correcta el conjunto de datos inicial ya que cada vez que re ejecute mi script, vuelve a hacer ese sampleo aleatorio.

>Para solucionar este problema, Sklearn ha introducido el parámetro **shuffle** en la función **train_test_split**.

```python
# Si shuffle=False, el conjunto de datos no mezclará antes del particionado
train_set, test_set = train_test_split(df, test_size=0.4, random_state=42, shuffle=False)
```

Ver video Caso práctico: división de conjunto de datos.

>stratify=df["protocol_type"] lo que hace es mantener las proporciones en los 2 subconjuntos, o sea mantiene la proporción de valores para el conjunto de datos original.
>
>Lo bueno de utilizar esto es que no va hacer ese sampleo aleatorio, lo que básicamente hará que nuestro conjunto de datos no se van a generar cada vez que reejecutemos nuestro script 

>Aseguramos que se mantengan las proporciones de determinadas características de entrada en los 3 sub conjuntos de datos #Train_Set #Test_Set #Validation_set de manera que nos aseguremos de que no hay ningún valor de esas características de entrada que quede sin representación en alguno de estos 3 subconjuntos de datos en los que subdividimos el conjunto de datos original

Dependiendo de lo que queramos resolver, en algunos casos será útil aplicar **stratify sampling** y en otros casos no, sólo bastaría con aplicar el particionado aleatorio directamente.

- Si tenemos un conjunto de datos muy grande, con ese particionado aleatorio sin aplicar stratify sampling, sería suficiente.
- Si tenemos un caso en el que hemos recopilado datos y de esos tenemos algunos ejemplos como 20 ejemplos que para la característica de entrada X2 tienen un valor determinado, probablemente tendremos que realizar stratify sampling sobre esa característica de entrada para asegurarnos que de esos 20 ejemplos que tienen un valor determinado, una proporción de ellos se queda en el #Train_Set , otra en el #Validation_set y otra proporción en el #Test_Set 

Esto es porque si hacemos una partición aleatoria es probable que esos 20 ejemplos queden en un sólo subconjunto o en 2 quizás, y es necesario particionarlos de manera que se distribuyan de manera regular en los 3 subconjuntos, sino no tendremos subconjuntos representativos del problema y tanto la validación como el entrenamiento no serían técnicas fiables.



