2025-07-12 16:31

**Tags:** #machine_learning #aprendizajeSupervisado  #Regresión_logística #regresión #Regresión_lineal #algoritmo_clasificación #threshold #función/hipótesis  #Función_sigmoide #funcion_deCoste_error #funcion_optimización 
### SECCIÓN 6 - REGRESIÓN Y CLASIFICACIÓN 

###### **References:**
-  **Índice:** [[CURSO MACHINE LEARNING]] 
- [[Qué es Machine Learning]]
- [[Qué es Machine Learning#Sección 5 - Clasificación de los sistemas de Machine Learning]]
- [[Qué es Machine Learning#**Aprendizaje Supervisado** aprendizajeSupervisado]]
---
#### ALGORITMO DE REGRESIÓN LOGÍSTICA #Regresión_logística  
[[#Función Hipótesis o modelo]]
[[#**FUNCIÓN HIPÓTESIS** de Regresión_logística]] #función/hipótesis #threshold 
[[#FUNCIÓN HIPÓTESIS - Regresión logística Regresión_logística]] #Función_sigmoide 
[[#FUNCIÓN DE COSTE - Regresión_logística]]
[[#**FUNCIÓN DE OPTIMIZACIÓN** - Regresión_logística]]

El algoritmo basado en regresión logística, a diferencia del algoritmo de regresión lineal que veníamos viendo, se va a **caracterizar** porque va a tratar de **predecir un valor discreto** por eso a veces se ve referido este tipo de **algoritmo como Algoritmo de Clasificación**. 

**Se caracteriza:** 

- Es un algoritmo **basado en un aprendizaje supervisado**, al igual que el algoritmo de regresión lineal, lo que quiere decir que va a recibir un **conjunto de datos etiquetados**, este se caracteriza porque tiene los **valores de entrada y los valores de salida**. 

 - Es un algoritmo basado en **Aprendizaje basado en modelos**, lo que quiere decir que van a **construir un modelo o una función/hipótesis** (al igual que el algoritmo de regresión lineal). 

- Se va a corresponder también con un **modelo lineal**, no es un modelo lineal puro sino que es un **modelo lineal generalizado**. 

>Va a **construir también una función/hipótesis** que también **será lineal**, al menos cuando lo construyamos con 1 o 2 características, por lo tanto, **nos vamos a quedar con que se corresponde con un modelo lineal**. 

- También van a **realizar predicciones computando una suma ponderada de las características de entrada y sumándole una constante conocida como bias** (recordar que en el algoritmo de regresión lineal, esta constante **bias era el tetha 0** que nombrábamos en la función hipótesis de la regresión lineal), pero aquí habrá una:

>**diferencia**, y es que al **resultado de esa función o de esa suma ponderada** se le va a **aplicar una función logística** y es por ello por lo que **recibe el nombre de regresión logística** 

- Lo que más diferencia este algoritmo de la regresión lineal es que Intenta **predecir valores discretos, mientras que a regresión lineal trataba de predecir valores continuos**, es decir, valores que se encontraban dentro de un rango muy amplio de valores como el costo de un determinado incidente de seguridad, en este caso los algoritmos basados en regresión logística van a tratar de predecir valores discretos, es decir **valores que se van a encontrar dentro de un rango acotado, como por ejemplo si un correo electrónico es spam o no lo es**.

---
### Función/Hipótesis o modelo 
[[#ALGORITMO DE REGRESIÓN LOGÍSTICA Regresión_logística]]

El modelo que construyen los algoritmos de regresión logística. 

Vamos a usar el **ejemplo de la detección del correo electrónico spam**, recordar que para poder construir un filtro de spam basado en técnicas de aprendizaje automático, lo **primero** que teníamos que hacer era **recoger un conjunto de datos**, como dijimos que la #Regresión_logística es un algoritmo que se basa en #aprendizajeSupervisado, lo primero que el analista debería hacer si quiere utilizar u algoritmo de regresión logística para predecir si un correo es spam o no, será **recoger un conjunto de correos electrónicos que formarán parte de nuestro conjunto de datos de entrenamiento y clasificarlos como Spam o No Spam**. 

Entonces recogemos ese conjunto de correos, **extraemos unas variables de entrada** (en este caso la única variable de entrada o características de esos correos que vamos a extraer **será el número de signos de interrogación y exclamación** porque consideramos que cuando un correo es Spam tendrá un número elevado de estos signos), y **también vamos a catalogar esos correos que se encuentran en nuestro conjunto de datos de entrenamiento** (los vamos a catalogar como spam o no spam). 

Nuestro **objetivo final:** 
>Es que, proporcionándole únicamente el número de signos de interrogación y de exclamación de un correo electrónico que llega a nuestra bandeja de entrada a nuestro algoritmo de regresión logística, **él sea capaz de decirnos si ese spam es legítimo o no en base a ese conjunto de datos de correos electrónicos etiquetados que le hemos proporcionado para que construya esa función hipótesis** que nos permite predecir. 

En el gráfico **tenemos 2 posibles valores en el eje Y** (que serían **Spam o no Spam**). En concreto, los problemas de clasificación suelen estar en un rango de valores muy acotado, en este caso **valores entre 0 y 1**. 

**Por lo general:** 

- el **0** se considera como la **clase negativa (correos No Spam)** 

- el **1** se considera como la **clase positiva (Spam)** 

Estos datos que tenemos en el gráfico son nuestro **conjunto de datos etiquetados**. 

>La **función/hipótesis o modelo** que va a generar el algoritmo de #Regresión_logística se va a corresponder (como ya vimos) con una **función lineal** que va a **tratar de predecir cuándo un correo electrónico es Spam o no**, o cuando un ejemplo en particular de manera genérica pertenece a una de las clases que se encuentran en ese rango acotado de valores. 

>Como vemos aquí, **este algoritmo nos va a predecir un valor concreto discreto, siempre un valor dentro de un rango**, por lo tanto, en este ejemplo va a tratar de predecirnos todos los correos que caigan de un lado del gráfico (un determinado lugar de la función) **los va a predecir como correos Spam, y todos los que caigan en el otro lado de la función los va a predecir como correos No Spam**. 

##### **Construcción de esta función para que sea capaz de predecir entre 2 valores y no entre un rango más amplio**

Como ya vimos hay una serie de pasos que tenemos que hacer para ir construyendo esa función/hipótesis o modelo en este tipo de #aprendizajeSupervisado algoritmos supervisado y **basado en un conjunto de datos de entrenamiento etiquetado**. 

1. **Recopilar nuestro conjunto de datos etiquetados**, y este tendrá unas características muy similares a las que vimos con el algoritmo de regresión lineal.  

Podemos **representar los datos en una tabla de 2 dimensiones** que de **manera práctica se convertirá en un data frame**, concretamente extrayendo un único valor (es decir, para una sola característica) de los correos, en este caso el número de signos de interrogación y exclamación, tendríamos una tabla donde: 

X = variable de entrada 

Y = Variable de salida 

Al tratarse de un conjunto de datos etiquetados tendríamos también la variable de salida, es decir si ese correo es Spam o no lo es.  

X1: número de signos de exclamación que extraemos de los correos 

Y: Spam o No Spam 

|         | X1  | Y   |
| ------- | --- | --- |
| Email 1 | 10  | 1   |
| Email 2 | 1   | 0   |
| Email 3 | 17  | 1   |
| Email 4 | ..  | ..  |

Para cada uno de estos emails le extraemos el número de signos de exclamación y de interrogación, por ejemplo, que el email 1 tenga 10, analizamos el correo y lo clasificamos y se determina después del análisis que es Spam. 

Así con todo el conjunto de datos hasta que tengamos la tabla completa y hayamos analizado todos los correos que forman parte de nuestro conjunto de datos. 

- **Respecto a las características de entrada (X) es lo mismo que la #Regresión_lineal:**
>Como vemos, no hay mucha diferencia respecto a la #Regresión_lineal, las **variables de entrada las determinamos con una X**, en este caso tenemos sólo una característica que extraemos, o sea sólo x1, pero si extrajéramos más características tendríamos más de un X, un X1, X2, X3, ..., Xn, y así vamos agregando más columnas a nuestro data frame. 

- **Lo que cambia es la variable de salida (Y):**
>Uno de los **cambios que tiene respecto al conjunto de datos**, es que Y se va **acotar a un rango mucho más reducido de valores**. 
>Los problemas de **Clasificación o de #Regresión_logística** que se encuentran **acotados en un rango de 2 valores se denominan problemas de Clasificación Binaria**. 

Mientras que los problemas donde Y se encuentre en un **rango más amplio de valores** (0, 1, .., n4) se van a determinar como **problemas de clasificación multiclase.**

###### **FUNCIÓN HIPÓTESIS** de #Regresión_logística 
Una vez visto cómo podemos denominar los diferentes aspectos del conjunto de datos de un algoritmo de regresión logística, vamos a hablar sobre la #función/hipótesis

La #función/hipótesis de la #Regresión_lineal venía parametrizada por los 2 parámetros theta 0 y theta 1. 

>Imaginemos que **tratamos de aplicar esta función hipótesis de la regresión lineal a nuestros problemas de #algoritmo_clasificación**, es decir, **vamos a utilizar la misma función hipótesis de la #Regresión_lineal que se supone que trataba de predecir un valor continuo**, para en este caso, **predecir un valor discreto** (o sea vamos a aplicarlo en un problema de clasificación o problema de #Regresión_logística concretamente para la detección de correos de spam). 

Entonces pasamos por todos los ciclos que vimos en el apartado anterior y, después de utilizar la #funcion_deCoste_error, después de usar la #funcion_optimización para minimizar ese error y buscar los parámetros óptimos, llegamos a unos **parámetros theta0 y theta1 óptimos que me generan concretamente una #función/hipótesis para este conjunto de datos** (una recta htheta (x) en el gráfico que se genera para ese conjunto de datos) suponiendo que utilizo la #función/hipótesis de la #Regresión_lineal y la ajusto en base a los datos que tenemos aquí. 

Son todos **datos que están en el 0 o en el 1 en el eje Y**, con lo cual si intentamos ajustar esta tendencia del conjunto de datos, una recta con la #función/hipótesis de la #Regresión_lineal, nos acabaría quedando un modelo similar al que vemos en el gráfico (una recta que pasa entre las cruces ubicadas entre los valores 0 y 1, clase 32 minuto 2.10) 

Htheta(x) = theta0 + theta1X        Htheta(x) = función hipótesis (recta del gráfico) 

>Una vez que hemos encontrado esos valores óptimos para theta0 y theta1 para esta función hipótesis de la regresión lineal y la hemos ajustado a nuestro conjunto de datos, ya con este modelo generado a partir de la función/hipótesis de la regresión lineal podríamos empezar a realizar predicciones. 

**Ejemplo:** 
Imaginemos que nos llega un correo a nuestra bandeja de entrada, extraemos el número determinado de signos de exclamación e interrogación (característica de entrada X), cae en un punto del eje X, hacemos la predicción extrapolando hasta la recta de la función y vemos que la predicción de esa función sería aproximadamente 0.6, y tiene sentido porque dijimos que con la función/hipótesis de regresión lineal obtenemos una predicción con un valor continuo, por lo tanto, o podemos pretender que utilizando la misma función hipótesis de la regresión lineal, el resultado sea 1 o 0. 

A nosotros en nuestro caso, no nos va a servir un valor continuo porque en nuestra predicción el resultado que queremos concretamente tiene que estar acotado dentro de ese rango de valores entre 0 (no spam) y 1 (spam), 0.6 no sabríamos interpretarlo en este caso. 

**Para esto usamos el #threshold o límite que nos dice:** 

- Si la predicción de nuestra función hipótesis es > 0.5 -> Y = 1 

- Si la predicción de nuestra función hipótesis es < 0.5 -> Y = 0 

Entonces en nuestro gráfico en el eje Y marcamos el 0.5 como recta #threshold y así delimitamos y decimos que básicamente todo lo que se encuentre hacia la izquierda de la función será No spam (0), y todo lo que se encuentra del lado derecho de la función será Spam (1). 

Con esto parecería que no necesitaremos otra función, o sea no necesitaríamos un algoritmo de regresión logística con una función hipótesis diferente a la de la regresión lineal, parecería que sólo necesitamos la función de la regresión lineal que conocemos y añadirle el #threshold. 

**Sin embargo, hay algunas consideraciones que no tuvimos en cuenta:** 
Imaginemos que en el gráfico tenemos algunos de los valores del eje Y en 1 más a la derecha, con esos 2 valores de entrenamiento que se encuentran más a la derecha tratamos de generar esa función hipótesis buscando de nuevo esos parámetros theta0 y theta 1 óptimos, nuestra función hipótesis sería una recta diferente que pasaría por otra parte del gráfico para tratar de ajustarselo máximo posible a ese nuevo conjunto de datos, en este caso al tener datos más a la derecha la pendiente será un poquito menos inclinada, entonces al establecer el #threshold en 0.5, ahora vemos que cae en otra parte de la pendiente, vemos que ahora la clasificación es diferente porque al haber movido esa pendiente como consecuencia de esos 2 ejemplos del conjunto de datos de entrenamiento que se encontraban más alejados, cuando ahora realizamos la predicción, nuestra función hipótesis para clasificar ahora nos dirá que ese nuevo correo que entró es No spam dependiendo de esa recta y el nuevo #threshold, lo cual es erróneo en este caso. 

>Por lo tanto, podemos ver que **cuando hay ejemplos que están alejados**, esta función/hipótesis de la #Regresión_lineal **se distorsiona y comienza a realizar malas predicciones**. 

>Por eso para problemas de #Clasificación **no podemos realizar la #función/hipótesis de la #Regresión_lineal**, por lo que necesitamos la #función/hipótesis de la #Regresión_logística. 

Otra incoherencia al tratar de usar este modelo de regresión lineal es que si recibimos un correo con un número muy elevado de entrada X (número de signos de interrogación...), al extrapolar hasta la función de la recta veríamos que nos dará incluso un valor de Y superior a 1...y eso no tiene sentido porque el rango de valores que debería recibir este modelo es un rango acotado entre 0 y 1.

#### FUNCIÓN HIPÓTESIS - Regresión logística #Regresión_logística 
[[Regresión Logística - Aprendizaje Supervisado#ALGORITMO DE REGRESIÓN LOGÍSTICA Regresión_logística]]

Para esta función hipótesis de la regresión logística, una de las cosas que nosotros queremos que sea capaz de hacer es que la predicción de esta función se encuentre dentro del rango entre 0 y 1, porque en este caso estamos hablando de un problema de clasificación binaria por lo que los valores posibles son o 1 o 0. 

>**¿Cómo va a lograr la #función/hipótesis de la #Regresión_logística limitar el resultado o la predicción de esa función hipótesis de la regresión lineal para que el valor se encuentre comprendido entre 0 y 1?** 

Lo hará **aplicando una función de activación** que se va a denominar #Función_sigmoide que la representamos mediante la **letra G**, se representa como se ve en el gráfico (clase 33, minuto 3.30), en el **eje Y tendríamos g(z), en el eje X tendríamos z**. 

###### **¿Cómo va a funcionar la aplicación de esta #Función_sigmoide a la #función/hipótesis que veíamos con la que se correspondía de la regresión lineal?**  

Básicamente la aplicación va a consistir en **limitar el resultado de ese Htheta(x) a un valor comprendido entre 0 y 1**. 

**Ahora veremos sobre la #Función_sigmoide:** 

¿Por qué usamos la función sigmoide, en qué va a consistir aplicarla a esa función hipótesis que veíamos para la regresión lineal?  


###### **Consideraciones principales de la #función/hipótesis de la #Regresión_logística**. 
Vamos a hablar sobre cómo se interpreta el resultado que nos proporciona la función hipótesis de la regresión logística. 

Ahora cuando hablamos de la htheta(x) ya no estamos hablando de la función hipótesis de la regresión lineal, sino que estamos hablando de que htheta(x) se corresponde con la función sigmoide (g) aplicado a theta0 + theta1X. 

Htheta(x) = g(theta0 + theta1X) 

O sea, Htheta(x) ahora se corresponde con la función hipótesis de la regresión logística.  

>Hay que tener en cuenta que esta #función/hipótesis lo que va a devolvernos es una **probabilidad de que Y sea igual a 1 para una entrada X**. 

O sea, nos va a **devolver la probabilidad de que ese ejemplo en concreto sea o pertenezca a la clase positiva en nuestro caso**, que sería a la clase Spam (y = 1). 

> La #función/hipótesis que construye la #Regresión_logística es una #función_lineal a la que se le aplica una #Función_sigmoide para que los valores queden en un rango acotado entre 0 y 1.


Es decir, esta #función/hipótesis nos va a seguir devolviendo un **valor continuo**, en este caso ese valor continuo estará **comprendido entre 0 y 1** y no tendríamos los problemas como dijimos arriba de que ejemplos anómalos distorsionen nuestra función hipótesis o modelo ni tampoco de un correo por ejemplo con un número elevado de X (signos de exclamación e interrogación) o con una variable de entrada muy grande produzca una predicción que se salga del rango de valores discretos que teníamos para la Y. 

Entonces vamos a predecir un valor continuo, pero:
>nosotros **queremos predecir un valor discreto**, o sea, queremos que nuestra **Y sea 0 o 1**, que nuestro algoritmo sea capaz de predecir entre esos 2 valores nada más (spam o No spam). 

Algunas consideraciones sobre el valor que es capaz de predecir, al final dijimos que lo que va a predecir es la **probabilidad de que ese ejemplo que le estamos pasando con esas variables de entrada sea la clase positiva**, donde cuando nosotros recibamos un nuevo correo, le vamos a extraer la variable de entrada X (el número de signos de interrogación y exclamación), se los vamos a pasar a la función hipótesis construida una vez que ajustados los parámetros theta0 y theta1 de la regresión logística, y lo que nos va a devolver es la probabilidad de que ese correo en concreto sea un correo de Spam, es decir que pertenezca a la clase positiva 

**También podemos calcular la probabilidad de que pertenezca a la clase negativa**, o sea de que sea un correo No spam. 

**Esto se hace básicamente porque:** 

**P(Y=0) + P(Y=1) = 1** 

**P(Y=1) = probabilidad de que pertenezca a la clase positiva** 

**P(Y=0) = probabilidad de que pertenezca a la clase negativa.** 

La probabilidad de que pertenezca a la clase negativa + la probabilidad de que pertenezca la clase positiva siempre tiene que ser igual a 1. 

Por lo tanto, si queremos calcular la probabilidad de que pertenezca a la clase negativa, básicamente despejamos de la ecuación P(Y=0) = 1 - P(Y=1). 

Como la predicción del algoritmo es básicamente la probabilidad de que pertenezca a la clase positiva, pues lo único que tenemos que hacer es 1 menos la predicción de ese algoritmo (htheta(x)), o sea de la función hipótesis para ese ejemplo en concreto. 

>Sin embargo, seguimos teniendo el **problema de que nos devuelve un valor continuo** y necesitamos que nos devuelva un valor discreto, nos devuelve una probabilidad, no un valor discreto y **no nos dice realmente si es spam o no spam, simplemente nos dice que es una probabilidad de que sea spam**. 

>Por lo tanto, tenemos que **encontrar alguna forma de que esa probabilidad se transforme en un valor discreto, para que el resultado final sea un 0 o un 1**. 

>Para ello, vamos a usar el **mismo truco que usamos para la regresión lineal**, vamos a utilizar un #threshold. 

Y este nos va a decir si la predicción **Y es >= 0.5**, voy a considerar que ese correo es Spam. **Y = 1** 

**Si la predicción Y es < 0.5**, digo que ese correo es **No Spam. Y = 0.** 

O sea, #threshold: 
>Si la probabilidad es >=0.5 digo que ese correo es Spam. 

>Si la probabilidad es < 0.5 ahí considero ese correo No Spam. 

Por lo tanto, para la #función/hipótesis de la #Regresión_logística, al **darnos un valor continuo (una probabilidad) es necesario aplicar un #threshold para transformarlo en un valor discreto**.

---
##### Interpretación del Resultado de la función Hipótesis de la regresión logística: 
(clase 34) 
>Ya conocemos algunos detalles técnicos sobre la función hipótesis de la regresión logística como, por ejemplo, sabemos que la #función/hipótesis de la #Regresión_logística se corresponde con la #Función_sigmoide **(g)** aplicado a ese theta0 + theta1X. 

También vimos cómo representar gráficamente la función sigmoide, donde vemos que en el eje Y tenemos g(z) que se corresponde con la función sigmoide aplicada a un término Z, mientras que en el eje X teníamos ese término Z. 

Podemos extender ese término de g(z), es decir, la función sigmoide aplicado a un término Z podemos extenderlo a la función hipótesis de la regresión logística, donde el término z sería ese término (theta0 + theta1X).  

Con lo cual, podemos representar los ejes de esta función gráfica básicamente en el eje Y como htheta(x), que sería igual a g(z) porque e exactamente la función sigmoide aplicada a un término z. 

Mientras que en el eje X tendríamos theta0 + theta1X, que sería exactamente ese término Z al cual se le aplica esa función sigmoide. 

>También vimos que la #función/hipótesis de la #Regresión_logística, aunque nos proporcionaba un **valor que se encontraba en un rango entre 0 y 1**, seguía proporcionándonos un valor continuo,
>por lo que teníamos que **aplicar un #threshold** para **transformar ese valor continuo en un valor discreto**, y para hacer esto poníamos como punto que esa función sea mayor o menor o igual a 0.5 y dependiendo de eso será 1 o 0, si es por ejemplo 0.8 será transformada en 1, si es 0.4 será transformada en 0, así transformamos el valor continuo en discreto. 

- Ver explicación clase 34 

**EJEMPLO:**
Supongamos que nuestro conjunto de datos de correos electrónicos **tiene 2 variables de entrada** y no una única variable de entrada. 

O sea, por un lado, nuestro conjunto de datos de correos tendrá el número de signos de exclamación e interrogación y por otro lado, también vamos a extraer el número de tags de HTML. 

Es decir, nuestro conjunto de datos tendrá 2 variables de entrada y la variable de salida. Recibimos un nuevo correo y recogemos el número de tags y el número de signos de interrogación y exclamación y ese será el conjunto de datos que le proporcionaremos a nuestro algoritmo de regresión logística para que ajuste esos parámetros de theta0 y theta1 a su valor óptimo, que sería el valor en el que la función hipótesis se ajuste lo mejor posible a la distribución de nuestro conjunto de datos. 

Nuestro conjunto de datos ahora tendrá entonces, 2 características y básicamente si lo representamos gráficamente, será como vemos en la slide, donde por un lado tendremos círculos que se corresponderán con los correos de No Spam, y tendremos las X que se corresponden con los correos Spam. 

O -> No Spam 

X -> SPAM 

2 variables de entrada para cada correo electrónico y 1 variable de salida que en este caso es SI es Spam o No Spam, es decir 0 o 1. 

(Ver video). 

Imaginemos que realizamos todo el proceso del cálculo del error, todo el proceso de optimización de ese error sin necesidad de conocer cómo es exactamente la función de error de la función de error de la regresión logística, simplemente imaginemos que pasamos por todo ese proceso y llegamos a encontrar los parámetros theta0, theta1 y theta2 óptimos que generan esa función hipótesis que mejor se va a adaptar a nuestro conjunto de datos.  

Imaginemos entonces que esos valores son los siguientes: 

Theta0= -9 

Theta1 = 1 

Theta2 = 1 

Si sustituimos estos valores en la función de la recta sigmoide (ver video) y nos da como resultado un valor >= 0, esta función predice y nos está diciendo que Y = 1. 

Esta sería una parte de la función hipótesis que se construiría una vez que nosotros ya hemos ajustado esos parámetros theta a su valor óptimo. 

Ver explicación video.
>Resumen:
>Nuestra #función/hipótesis se adapta a la tendencia de nuestros datos pero no nos sirve que se adapte de la manera en que se adaptaba a la #Regresión_lineal que de una forma similar a una recta lineal pasando por el medio por ejemplo, sino que, tiene que adaptarse de manera que separe los conjuntos de datos porque esto es una tarea de #clasificación 

---
#### FUNCIÓN DE COSTE - #Regresión_logística  
[[#ALGORITMO DE REGRESIÓN LOGÍSTICA Regresión_logística]]

Haremos un **repaso** de la #funcion_deCoste_error que veíamos para los algoritmos de #Regresión_lineal:  

Cuando representábamos gráficamente esta #funcion_deCoste_error veíamos que era algo similar a una **parábola invertida** donde en el eje Y teníamos la función de costo J(theta) y en el eje X teníamos theta, y la #función/hipótesis a la que aplicábamos esta función de coste básicamente era la función de la #Regresión_lineal. 

>Lo que tratábamos de hacer con esta #funcion_deCoste_error era **minimizarla a través de un algoritmo de optimización** que llamábamos #gradientDescent. 

>Este algoritmo de #funcion_optimización lo que trataba de hacer era **buscar el mínimo de esa #funcion_deCoste_error**, para eso iba haciendo una especie de descenso de gradiente basándose en la pendiente. 

#Regresión_logística :
Cuando intentamos representar esta misma #funcion_deCoste_error que teníamos para la #Regresión_lineal, pero aplicándole a la #función/hipótesis de la #Regresión_logística (que es la #Función_sigmoide) tendríamos representado gráficamente como se muestra en el video. 

> También nos interesa en este caso **alcanzar ese punto mínimo u óptimo global de la función**, pero **no podemos usar la #funcion_deCoste_error de la #Regresión_lineal porque esta genera óptimos locales (no llegan a ser el óptimo global) para la regresión logística y corremos el riesgo que el valor de los parámetros quede mal ajustado** como consecuencia de haber caído en un óptimo local pensando que está en ese óptimo global cuando no es así. (VER VIDEO). 

> Por lo tanto, no podemos usar la #funcion_deCoste_error de la #Regresión_lineal para la #Regresión_logística 

###### **Para la #Regresión_logística usamos otra #funcion_deCoste_error.** 

También es necesario encontrar los parámetros theta0 y theta1 que mejor se ajusten a la tendencia de nuestros datos, esos parámetros tienen que estar bien ajustado para que el modelo o el algoritmo realice buenas predicciones. 

Esta serie de funciones son importantes para medir el error que produce nuestro algoritmo cuando realiza una predicción. 

Vimos que cuanto más nos acercábamos a esa predicción Y = 0, y si esa predicción era correcta, el error iba disminuyendo. 

##### **Resumen:** #funcion_deCoste_error #Regresión_logística 

>Son 2 funciones #funcion_deCoste_error que usamos para la #Regresión_logística porque:
>
>Si nuestro ejemplo dentro de nuestro conjunto de datos está etiquetado con la **clase + (Y=1)**, entonces nuestra función es  
> **->** para Y = 1, error = -log(htheta(x))
> 
> Si nuestro ejemplo dentro de nuestro conjunto de datos está etiquetado con la **clase - (Y= 0**), entonces nuestra función es:
> -> para Y = 0, error = -log(1 - htheta(x))
 
>Tenemos estos 2 términos dependiendo de si ese ejemplo de entrenamiento se encuentra etiquetado con una clase o con otra.

 >QUEREMOS TENER UNA ÚNICA FUNICÓN DE ERROR #funcion_deCoste_error 
 >Para esto pondremos estos 2 términos en una única función
  
- **Ver video explicaciones función de coste 1 y 2** 

>Resumiendo, la #funcion_deCoste_error  nos sirve para **calcular si la predicción que realiza nuestro algoritmo es correcta o no en base a la etiqueta que tiene ese ejemplo en nuestro conjunto de datos**. 

Nos da un ejemplo para el cual estaríamos evaluando el error de una predicción para un ejemplo con una determinada etiqueta, primero nos da un ejemplo suponiendo que nuestro ejemplo pertenece a la clase positiva dentro de nuestro conjunto de datos, por lo que ese ejemplo lo tendríamos como Y = 1 o etiquetado como Y = 1 dentro de nuestro conjunto de datos. 

Esa función de error o de costo vamos a utilizar para el algoritmo de regresión logística y concretamente junto con una función de optimización, para obtener el valor óptimo de los parámetros theta0, theta1, thetaN. 

---
#### **FUNCIÓN DE OPTIMIZACIÓN** - #Regresión_logística 
[[#ALGORITMO DE REGRESIÓN LOGÍSTICA Regresión_logística]]

La #funcion_optimización la vamos a **utilizar para obtener el valor óptimo de los parámetros theta0, theta1, thetaN**, ya que estos parametrizan la #función/hipótesis de la #Regresión_logística. 

>La #funcion_optimización que usaremos será la **misma que usábamos para la #Regresión_lineal** y se va a corresponder con #gradientDescent .

>**Usamos la #funcion_deCoste_error de la #Regresión_logística :** 
>Que se correspondía con la unión de esos 2 términos para formar una única #funcion_deCoste_error. 

Tendremos como en los ejemplos anteriores, 2 variables de entrada X1 y X2 y una de salida Y. Con estas características podemos representar una función hipótesis para la regresión logística. 

>Recordando:
 #gradientDescent lo que iba haciendo era ir **reduciendo el valor o acercando el valor de esos parámetros al valor óptimo global**. 
   Hacíamos una **inicialización de esos parámetros de manera más o menos aleatoria** y lo que hacíamos con la #funcion_deCoste_error era **calcular el error que había respecto a la predicción que debía estar dando con nuestro conjunto de datos de entrenamiento**, y de esa manera íbamos **ajustando el valor de esos parámetros con #gradientDescent** de manera iterativa restándole la pendiente de la función para que **llegase a ese óptimo global de manera matemática**. 

Con la #funcion_deCoste_error se va **modificando theta0 hasta que llega a un punto en el que theta0 no variase o variara muy poquito y ahí llegamos a la conclusión de que llegó a ese valor óptimo global**. 
Lo **mismo para theta1**. 
Se van **ajustando esos parámetros** hasta que lleguen a sus valores óptimos globales. 

#gradientDescent lo que hará es que, en **función de estas ecuaciones de error** para **ajustar los parámetros, irá variando los parámetros theta0 y theta1** conforme a las ecuaciones para cada uno de ellos usando los valores de nuestro conjunto de datos. 
Así se llega a la #función/hipótesis del modelo que **mejor se ajusta al conjunto de datos de entrenamiento que le hemos proporcionado**.







