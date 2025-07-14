2025-07-11 12:59

**Tags:** #machine_learning #aprendizajeSupervisado #regresión #Regresión_lineal #funcion_deCoste_error #funcion_optimización 

### SECCIÓN 6 - REGRESIÓN Y CLASIFICACIÓN 

###### **References:**
-  **Índice:** [[CURSO MACHINE LEARNING]] 
- [[Qué es Machine Learning]]
- [[Qué es Machine Learning#Sección 5 - Clasificación de los sistemas de Machine Learning]]
- [[Qué es Machine Learning#**Aprendizaje Supervisado** aprendizajeSupervisado]]
---

>**Resumen:** 
>2 de sus algoritmos más sencillos son el algoritmo de #Regresión_lineal y el algoritmo de #Regresión_logística. 

>**Estos 2 algoritmos nos van a permitir predecir:
>- valores continuos** (es decir, que se encuentren en un rango muy amplio de valores, en este caso será la #Regresión_lineal), y también predecir 
>- **valores discretos**, es decir, resolver problemas de #clasificación en este caso con el algoritmo de #Regresión_logística. 

---
#### ALGORITMO DE REGRESIÓN LINEAL #Regresión_lineal 
[[#**REGRESIÓN LINEAL FUNCIÓN/HIPÓTESIS**]]
[[#**REGRESIÓN LINEAL CONSTRUCCIÓN DEL MODELO**]]
[[#REGRESIÓN LINEAL FUNCIÓN DE COSTO O DE ERROR]]
[[#**REGRESIÓN LINEAL FUNCIÓN DE OPTIMIZACIÓN**]]

---

>Este es un **algoritmo basado en Aprendizaje Supervisado #aprendizajeSupervisado**, esto quiere decir que va a recibir un conjunto de **datos etiquetados** (donde nosotros vamos a tener que indicarle para cada uno de los ejemplos de nuestro conjunto de datos a qué categoría pertenece) 

>Por otro lado, es un algoritmo #aprendizaje_en_modelos basado en **Modelos**, lo que quiere decir que va a **construir una función/hipótesis o modelo** que **utilizará para realizar predicciones**. 

>Este modelo se va a corresponder con una **función o modelo lineales**, esto quiere decir, que al final la **función resultado será una línea**.

>Se corresponde con una técnica de regresión que **construye un modelo o una función/hipótesis lineal**. 

>Va a **realizar predicciones** computando una **suma ponderada de las características de entrada** y al final le va a sumar una **constante que se conoce como bias**. 

Este tipo de algoritmo va a intentar predecir **valores continuos**, esto quiere decir que, dentro del conjunto de las técnicas de aprendizaje supervisado, se clasifica en ese subconjunto que se corresponde con las técnicas de regresión. 

**EJEMPLO**
Por ejemplo, cuando tratamos de predecir el costo de un incidente de seguridad en base a una serie de características de entrada como el número de sistemas que se habían visto afectados en ese incidente de seguridad. 

Vamos a utilizar este tipo de algoritmos cuando nos encontremos con un conjunto de datos, es decir, un conjunto de experiencia pasada que se distribuya de una manera similar a la que vemos en el gráfico donde veremos la distribución de esos puntos (datos) después de reunir los datos de incidentes pasados con el número de equipos que se vieron afectados y el costo que tuvo ese incidente en el pasado. 

Esta distribución de los datos tiene una característica bastante particular y es que los **datos se están distribuyendo con una tendencia lineal**, es decir si agarro una función matemática lineal y la trato de ajustar a mi conjunto de datos y obtenemos la función que vemos en el gráfico (que es una línea recta), vemos que se ajusta más o menos bien a la tendencia que tienen nuestros datos. 

Esta **función/hipótesis o modelo será el tipo de función que va a construir el algoritmo de regresión lineal** y el objetivo de este algoritmo de #machine_learning será que proporcionándole únicamente los ejemplos de mi conjunto de entrenamiento, **construir esta función/hipótesis o modelo** ajustándolo automáticamente de la mejor manera posible a la tendencia de nuestros datos. 

Lo siguiente que vamos a hacer es tratar de definir la notación que vamos a estar utilizando. 

Si estamos frente a este problema donde estamos tratando de predecir el coste de un incidente de seguridad en base al número de sistemas que se vieron afectados, lo primero que vamos a necesitar es un conjunto de datos etiquetados, entonces nuestro conjunto de datos tendrá que estar formado por una serie de características de entrada que van a ser características que vamos a extraer de cada uno de esos incidentes pasados, y una característica de salida que será el valor que vamos a querer predecir que en este caso se corresponde con el costo del incidente. 

>Estas **características de entrada** están referenciadas como **features** **-> X**

>Las **características de salida** se verán referenciadas como **target value** -> **Y**

> Conjunto de datos = data set 

> Cada uno de los **ejemplos de nuestro conjunto de datos** se denomina como **(x,y) = ejemplo de entrenamiento** 

. i1 = incidente 1 
. in = último ejemplo, siendo **"n"** el n

| incidente | Número sistemas afectados (x) | Coste en euros (y) |
| --------- | ----------------------------- | ------------------ |
| i1        | 1000                          | 10000              |
| i2        | 1500                          | 20000              |
| i3        | 500                           | 5500               |
| ....      | ...                           | ...                |
| in        | 200                           | 2500               |
**Así hasta el incidente n siendo n el número de ejemplos de nuestro conjunto de datos** 

- La **característica de entrada:
Es el número de sistemas afectados**, es **X**, como es una sola característica es **X1**, si hubiésemos extraído más características de incidentes como por ej el número de vulnerabilidades o el tiempo que tardó en resolverse el incidente, ahí ya tendríamos más de una X, tendríamos **X1, X2, X3 y así hasta la última característica que hayamos extraído que será Xn**. 

- La **variable de salida será Y**: target value 

>**ejemplo de entrenamiento (x,y)**: 
>i3 | X = 500 | Y = 5500 
>
>Si tuviera x1, x2 y más características de entrada... 
  **nuestro ejemplo de entrenamiento (x,y)** sería:  
  **(X1,X2,X3,...,Xn, Y)**

---
##### **REGRESIÓN LINEAL: FUNCIÓN/HIPÓTESIS** 
[[#ALGORITMO DE REGRESIÓN LINEAL Regresión_lineal]]

Como venimos viendo, gran parte de las técnicas de #machine_learning, y sobre todo aquellas que se basan en #aprendizajeSupervisado, tienen un esquema bastante similar donde, por un lado, disponemos de un **conjunto de datos** (lo que llamábamos como datos de experiencia pasada), y este conjunto de datos se lo vamos a **proporcionar a una función matemática que suele denominarse función hipótesis**. 

Esta función matemática va a tener una **serie de parámetros que van a ir ajustándose con los datos** que se encuentran dentro de nuestro conjunto de datos dando como resultado lo que se denomina **MODELO**. 

>El **modelo no es más que la función/hipótesis después de haberse ajustado a la tendencia de los datos que hay en nuestro conjunto de datos. 

>El modelo será también lo que **utilizaremos posteriormente para realizar predicciones** 

**Esquema: **

Conjunto de datos —> Función/hipótesis --> Modelo --> Predicciones. 

- Ya hablamos sobre el **conjunto de datos que está asociado con el algoritmo de regresión lineal**. 

- Ahora vamos a focalizarnos en la **FUNCIÓN/HIPÓTESIS** que es la función matemática asociada con la regresión lineal. 

La **función/hipótesis** del algoritmo de #Regresión_lineal es la siguiente, y es la función de la recta  

**Y = mx + b**     #Regresión_lineal 

El algoritmo de regresión lineal construye una función lineal, en este caso es cuando tenemos una única característica de entrada (una única variable de entrada que sería X1) que en el ejemplo de incidentes de seguridad se correspondería con la primera característica de entrada que es el número de equipos afectados. 

Cuando represento la función/hipótesis de la regresión lineal, esa función y=mx + b es una representación genérica que podría ser una recta de diferentes maneras (distintas posibilidades).  

Entonces, qué es lo que determina que mi función matemática sea de una u otra manera. 

Lo que determina esto son los parámetros del modelo (sería mx y b) donde mx determina el punto en el que va a cortar con el eje Y, y b va a indicar la pendiente, es decir, la inclinación que va a tener nuestra recta. 

Con lo cual, lo que va a determinar concretamente la función matemática que va a construir este algoritmo, serán los parámetros del Modelo (theta 0 y theta 1, o mx y b). 

El objetivo será encontrar los valores óptimos de esos parámetros que ajusten lo mejor posible esa recta a la tendencia de nuestro conjunto de datos. 

>Cuando tenemos una única característica de entrada (X1), el algoritmo de regresión lineal se denomina **Regresión Lineal Univariable** y la funicón/hipótesis es la de  

**Hthetha(X) = thetha0 + theta1X**. 

>Si tuviéramos más características de entrada, o sea si en el ejemplo que venimos viendo hubiésemos recopilado más cosas aparte del número de equipos afectados, en este caso tendríamos x1, x2, x3.. Y se denomina **Regresión Lineal Multivariable**. 

Al tener varias variables, también cambia su función/hipótesis, la cual sería: 

Hthetha(X) = thetha0 + theta1X1 + theta2X2 + ...+ thetanXn (última característica de entrada) 

>La **principal diferencia** que hay es que tenemos más parámetros del modelo, mientras que en una **regresión lineal univariable** tenemos 2 parámetros del modelo, en el caso de una **regresión lineal multivariable** tendremos varios parámetros (theta1, theta2, y así sucesivamente hasta el número de características de entrada que tuviese). 

Otras de las afirmaciones que dijimos es que este algoritmo es una suma ponderada de sus entradas. 
Vemos efectivamente que la función del algoritmo de regresión lineal es una suma ponderada de las entradas, porque tenemos las entradas que sería X1, X2, Xn ponderadas por estos parámetros del modelo theta1, theta2, theta n, y le sumamos un término bias que sería theta0 

###### **¿Cómo se ajusta esta función matemática (función/hipótesis) a la tendencia de nuestro conjunto de datos?**

> Este ajuste de la función matemática a la tendencia de nuestros datos es lo que se denomina entrenamiento del algoritmo, sirve para construir el **MODELO.**

---
###### **REGRESIÓN LINEAL: CONSTRUCCIÓN DEL MODELO** 
[[#ALGORITMO DE REGRESIÓN LINEAL Regresión_lineal]]

#funcion_deCoste_error 
#funcion_optimización 

Tomando el ejemplo que venimos viendo, en el que habíamos recopilado datos de incidentes pasados, los representa en la recta de la clase. 

Imaginemos que los puntos morados en el gráfico se corresponden con los datos de incidentes pasados, de los cuales obtuvimos, por un lado, el número de equipos que se vieron afectados (representado como X1 en el eje horizontal) y hemos recopilado también el costo que tuvo el incidente de seguridad (representado como Y). 

Si queremos resolver el problema de tratar de predecir el costo que tendría un incidente de seguridad que tendría un incidente en el futuro en base al número de equipos que se vieron afectados utilizando el algoritmo de #Regresión_lineal, entonces tendremos que usar la **función/hipótesis de la regresión lineal univariable** (porque tenemos una única característica de entrada que sería el número de equipos que se vieron afectados) 

**h(theta)x = theta0 + theta1X1**  

>Aquí la clave es que, de alguna manera tenemos que **encontrar cuáles son los valores óptimos** de estos **parámetros theta0 y theta1** de manera que **nuestra función/hipótesis o función matemática se adapte lo mejor posible a la tendencia de nuestro conjunto de datos** de entrenamiento. 

Es decir, que construyamos una función/hipótesis similar a la línea en el gráfico donde theta0 estaría recibiendo el valor de 0 (porque estaría cortando por el eje vertical en el cero) y theta1 recibiría un valor cualquier como por ejemplo 1 o el valor que fuese. 

>De manera que **cuando reciba un nuevo número de equipos afectados y quiero predecir el costo del incidente**: 
>Lo que se hacer es tomar el número de equipos afectados y con mi función matemática realizaríamos una predicción que sería que para ese número de equipos afectados en función de esa función/hipótesis que construimos, debería tener un costo aproximado de (tomar valor de X, ir hasta la recta e ir hasta la variable Y y ver el valor); **esa predicción es correcta ya que se ha adaptado correctamente a la tendencia de nuestro conjunto de datos de entrenamiento**. 

Ejemplo: h(0) = theta (cero) + (un valor para theta 1, cualquier valor por ejemplo 1) esto multiplicado por X1 que sería el número de equipos afectados (200 por ejemplo) 

Y = 0 + 1 * 200 

Y = 200 (euros) 

(ver explicación video) 

>¿Cómo vamos a **encontrar el valor de los parámetros theta 0 y theta1 óptimos** que **mejor adapta nuestra función/hipótesis a la tendencia de nuestros datos**? 

#funcion_deCoste_error 
> Lo haremos utilizando una **función matemática que se denomina función de coste o función de error** y este es uno de los componentes principales de muchos de los algoritmos de #machine_learning, no es algo propio sólo de la regresión lineal. 

#### **¿Qué hace esta función de coste o función de error?** 
#funcion_deCoste_error

>Esta **función va a calcular el error que hay entre la predicción que debería estar realizando nuestro algoritmo para los ejemplos de nuestro conjunto de datos**, tener en cuenta que los ejemplos de nuestro conjunto de **datos están etiquetados**, esto quiere decir que yo sé que, para un determinado número de equipos afectados, debería darme una predicción Y, si veo que mi algoritmo en lugar de darme la predicción que se supone que me tiene que dar, me da otro valor, sabremos que ahí hay un error bastante grande. 

Este **error si lo representamos gráficamente estaría dado por la diferencia (distancia) entre el valor de Y para X que debería darme con el valor de Y que me da (si está mal hecha la predicción como decíamos arriba)**. 

#funcion_deCoste_error 
>Entonces eso es lo que hace la **función de costo o función de error**, va a calcular el error que hay entre todos los ejemplos de nuestro conjunto de datos con relación a la función hipótesis que hemos construido (recta) (ver explicación con gráfico en el video). 

Entonces #funcion_deCoste_error **este error nos indica si la función/hipótesis está bien ajustada**, y es necesario saberlo porque después vamos a utilizar otra función que se llama **función de optimización** 

#funcion_optimización 
>Se va a encargar de ir **modificando los parámetros theta0 y theta1 de manera que se minimice el error que calcula la función de costo**, o sea va a ir modificando esos parámetros para que nuestra **función hipótesis vaya cambiando hasta que se ajuste lo mejor posible a la tendencia de nuestros datos** o (lo que es lo mismo, hasta que el error que nos proporciona la función de costo no se pueda minimizar más, siempre dará un error aunque sea muy bajito). 

>**Estos parámetros se irán ajustando hasta que la función/hipótesis (recta) no pueda ajustar mejor a la tendencia de nuestros datos, en ese punto habremos terminado de ajustarla y de construir el modelo**

Con lo cual el algoritmo de #Regresión_lineal va a: 

**1)** Inicializar estos parámetros theta 0 y theta 1 de manera aleatoria, después va a 

**2)** Utilizar la #funcion_deCoste_error para **calcular el error de nuestra función/hipótesis ajustada con esos valores aleatorios de los parámetros** respecto a los ejemplos de nuestro conjunto de datos, y después va a

**3)** Utilizar una #funcion_optimización para **minimizar ese error de manera que vaya modificando theta0 y theta1 hasta lograr que la función/hipótesis se ajuste lo mejor posible a la tendencia de nuestros datos** o, lo que es lo mismo, hasta que el error que nos da la #funcion_deCoste_error ya no pueda disminuirse más. 

>TODO ESTE PROCESO QUE ACABMOS DE VER SE DENOMINA **ENTRENAR UN ALGORITMO DE #machine_learning**, CONCRETAMENTE UN **ALGORITMO BASADO EN #aprendizajeSupervisado** (ya que para poder calcular esta función de error vamos a requerir que nuestro **conjunto de datos esté etiquetado**, es decir que necesitamos **saber la variable de salida (Y)** de los datos que tenemos. 

---
### REGRESIÓN LINEAL: FUNCIÓN DE COSTO O DE ERROR 
[[#ALGORITMO DE REGRESIÓN LINEAL Regresión_lineal]]

Lo primero que tenemos que entender de las funciones de costo es que pueden variar, es decir, puedo aplicar diferentes funciones de costo a un mismo algoritmo de #machine_learning. 

Concretamente cuando hablamos de #Regresión_lineal, la función de costo que suele aplicarse es una que se denomina #MSE **Mean Square Error (MSE)**, se calcula el error, se eleva al cuadrado y se divide entre el número total de ejemplos del conjunto de datos de entrenamiento (que sería hacer la media). 

Lo que venimos viendo sobre este algoritmo de #Regresión_lineal, para repasar decíamos que este algoritmo inicializaba los parámetros theta0 y theta1 (para el ejemplo de regresión lineal univariable) de manera aleatoria. 

Por ejemplo, como vemos en el video, en el gráfico tenemos representado nuestro conjunto de datos y, cuando inicialicemos estos parámetros theta0 y theta1 se podría generar una función/hipótesis como por ejemplo la que vemos en el gráfico (una recta en el gráfico). 

>Una vez que hemos inicializado los parámetros y hemos generado la función/hipótesis (recta), lo siguiente que hacemos es utilizar la función de error para ver cómo de bien o de mal predice esta función/hipótesis que hemos generado. 

La función de error viene determinada por la siguiente ecuación: (ver video) 

Explicación: min 1.46

Si vemos el conjunto de datos representado, debemos tener en cuenta que cada uno de los puntos representa un ejemplo dentro de nuestro conjunto de datos, por ejemplo, un de los puntos podría ser (x1, y1) donde x1 representa el número de equipos afectados mientras que y1 representa el costo que tuvo, y así para todos los ejemplos (x2, y2), (x3, y3), etc. (VER VIDEO) 

>**Resultado:**
>Al final de todo lo que se resuelve en esta ecuación **obtenemos un número el cual determina el error general que está proporcionando esta función/hipótesis** que hemos construido utilizando un valor aleatorio de los parámetros theta0 y theta1. 

>Una vez que hemos **obtenido este error** (calculando como se explica en el video) lo siguiente que vamos a utilizar es la #funcion_optimización **para modificar el valor de estos parámetros de manera que el error que proporciona esta #funcion_deCoste_error** (ese número que se obtiene después del cálculo de esa ecuación) **vaya minimizándose**, o sea ese resultado que obtiene la función de error se vaya haciendo cada vez lo más pequeño posible hasta que llegue a un punto donde ya no pueda hacerse más pequeño. 

En ese punto habremos **minimizado al máximo la #funcion_deCoste_error y habremos obtenido el valor óptimo de los parámetros theta0 y theta1** (habremos ajustado esta función/hipótesis lo mejor posible a la tendencia de nuestros datos). 

>Importante quedarse con el concepto de que un algoritmo de #machine_learning va a utilizar la #funcion_deCoste_error para **evaluar qué tal se está comportando la función/hipótesis que ha construido respecto al conjunto de datos de entrenamiento** del que disponemos.

---
##### **REGRESIÓN LINEAL: FUNCIÓN DE OPTIMIZACIÓN** 
[[#ALGORITMO DE REGRESIÓN LINEAL Regresión_lineal]]

#funcion_optimización 
Lo que hace es ir optimizando esa #funcion_deCoste_error haciéndola cada vez más chica mediante la modificación de los parámetros.

>La función de optimización **sirve para modificar el valor de estos parámetros** **de manera que el error que proporciona** esta #funcion_deCoste_error (ese número que se obtiene después del cálculo de esa ecuación) **vaya minimizándose**, o sea ese resultado que obtiene la función de error se vaya haciendo cada vez lo más pequeño posible hasta que llegue a un punto donde ya no pueda hacerse más pequeño. 

Este es el último componente para comprender todo el proceso completo de aprendizaje del algoritmo de regresión lineal. 

>Podemos utilizar **varias funciones de optimización** con una misma técnica de #machine_learning, la función de optimización que **más se utiliza** con diferencia es una que se denomina **Gradient Descent**. #gradientDescent 

>**La #funcion_optimización estará muy ligada a la #funcion_deCoste_error que estemos utilizando con ese algoritmo.** 

Cuando hablamos de regresión lineal, la función de costo o de error que estamos utilizando es la que vimos en el video anterior (la ecuación). 

>Como ya dijimos, el **objetivo** de la #funcion_optimización será **minimizar el resultado** de esa #funcion_deCoste_error. 

>Lo que hace básicamente esta #funcion_optimización #gradientDescent es ir repitiendo el proceso de elegir un valor hasta que X ya no varía más. 
>Cuando X no varía en varias iteraciones quiere decir que hemos llegado al punto mínimo, es decir que encontramos el valor del parámetro (en este caso de X) que minimiza esta función de error. 

Se repite hasta que theta0 y theta1 no varíen.