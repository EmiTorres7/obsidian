2025-07-26 14:02

**Tags:**  #machine_learning #AI  #aprendizajeSupervisado #Regresión_lineal #Regresión_logística #función/hipótesis 

### Creación de un proyecto de Machine Learning 

###### **References:**
-  **Índice:** [[CURSO MACHINE LEARNING]] 
- [[Qué es Machine Learning]]
- [[Qué es Machine Learning#Sección 5 - Clasificación de los sistemas de Machine Learning]]
- [[Qué es Machine Learning#**Aprendizaje Supervisado** aprendizajeSupervisado]]
---
### 1.- CONJUNTO DE DATOS 
- [[#Consideraciones a tener en cuenta en un proyecto de Machine Learning]]
- [[#Recomendaciones sobre el Conjunto de Datos a la hora de afrontar un problema real mediante el uso de técnicas de machine_learning]]

#### Consideraciones a tener en cuenta en un proyecto de Machine Learning 

Vimos 2 de las técnicas más sencillas que podemos encontrar dentro del área del aprendizaje automático, #aprendizajeSupervisado que son la #Regresión_lineal y la #Regresión_logística. 

>En uno de los ejemplos prácticos, nuestro conjunto de datos fue generado por nosotros y tenía una única característica de entrada (el número de equipos afectados) y una característica de salida (el costo del incidente). 

>En casos reales, tendremos conjuntos de datos mucho más complejos, con un montón de atributos o características de entrada que representan ese problema. 

Por ejemplo, si tratamos de clasificar transacciones bancarias como fraudulenta o legítimas, básicamente vamos a extraer un montón de características de esas transacciones bancarias (cantidad que se ha transferido, la aplicación que se utilizó para realizar esa transacción, tiempo que llevaba esa cuenta activa, etc.), es decir un montón de X1, X2, X3, Xn. 

- Tendremos **muchos atributos o características de entrada** donde algunas pueden ser valores numéricos, otros caracteres de texto y así. 

- Y tendremos **una única etiqueta de salida** que será 0 o 1, es decir, si esa transacción es fraudulenta o legítima. 
 
>Por todo esto, es muy importante cómo tendemos que procesar y parsear ese conjunto de datos inicial, de manera que cuando le proporcionemos a nuestro algoritmo, este sea capaz de construir una función hipótesis ajustada, es decir, de encontrar esos parámetros theta0, theta1, thetaN óptimos que minimicen esa función de error. 

>Seleccionar un buen conjunto de datos tiene tanta importancia como seleccionar un buen algoritmo.

En la imagen veremos una gráfica de un ejemplo que se corresponde con un **sistema de corrector lingüístico** que corregía faltas de ortografía, problemas sintácticos, etc., entonces se entrenaron una serie de algoritmos (memory-based, winnow, perception, naive bayes) y evaluaron el rendimiento de estos algoritmos en función de la cantidad de datos que tenían en su conjunto de datos y que le proporcionaban para entrenar esa función hipótesis ajustada o ese modelo. 

**Gráfico**: 

- En el **eje X** tenemos el número de palabras, es decir, el tamaño del conjunto de datos que se utilizó para entrenar o construir esa función hipótesis de estos 4 algoritmos. 

- En el **eje Y**, tenemos la precisión que tenía ese algoritmo (Test Accuracy) una vez entrenado con más o menos datos de nuestro conjunto de datos. 

**Fijarse**: 

>La mayoría de los algoritmos empiezan con un **número pequeño de ejemplos en nuestro conjunto de datos de entrenamiento** y cuando los entrenamos con ese número pequeño, vemos que **sí hay bastante diferencia entre la precisión o rendimiento (Y) de estos modelos o algoritmos** a la hora de predecir. 

Por ejemplo, cuando tenemos un número pequeño de palabras para entrenar este tipo de algoritmos vemos cómo el algoritmo Winnow se comporta bastante peor que otros algoritmos como los algoritmos basados en memoria o perceptron, por lo que vemos que cuando usamos un conjunto de datos pequeño, tenemos bastante diferencia en la predicción. 

>Cuando le proporcionamos más y más datos de entrenamiento para construir esa función hipótesis para ajustar esos parámetros theta0 y theta1, o sea, a medida que **proporcionamos un conjunto de datos más grande.**.. más palabras (el conjunto de datos de entrenamiento en este caso está formado por palabras que están escritas de forma correcta, entonces el algoritmo aprende cómo es una palabra correcta y luego es capaz de corregir una que es incorrecta) lo que sucede es que **muchos algoritmos acaban en un rendimiento o en una predicción muy similar**, es decir, que da igual qué algoritmo seleccionemos entre los que tenemos (pareciera que el de memoria es el que proporciona los peores resultados pero a medida que le vamos proporcionamos más ejemplos de entrenamiento también llegaría a un punto en el que estaría en la misma situación que los otros 3 algoritmos). 

De forma que con esto vemos que da igual el algoritmo que seleccionemos de los que tenemos porque si tenemos un conjunto de datos lo suficientemente grande, al final todos los algoritmos, la mayoría de las técnicas de #machine_learning, acaban proporcionándonos una precisión o un rendimiento similar. 

>**Conclusión:** Esto quiere decir que, el **conjunto de datos** es una parte completamente esencial en la resolución de un problema mediante el uso de #machine_learning, es tan importante tener un conjunto de datos de experiencia pasada suficientemente grande y de calidad como tener o seleccionar un algoritmo que sea adecuado para resolver ese problema. 

Con un conjunto de datos suficientemente grande y representativo de ese problema, básicamente la selección del algoritmo es un problema secundario, porque como vemos, con un conjunto de datos grande, se van a comportar con una precisión similar a la hora de predecir para nuevos ejemplos. 

Por eso es **muy importante seleccionar el conjunto de datos y los preprocesamiento y análisis adecuados para proporcionárselo al algoritmo** para que este sea capaz de realizar una función hipótesis adecuada. 

En esa sección vamos a aprender: 

1. cómo tenemos que gestionar ese conjunto de datos,  
2. cómo pre-procesarlos,  
3. cómo transformar esas variables categóricas en variables numéricas
4. Cómo vamos a proporcionárselo a un algoritmo de #machine_learning para que le saque el mayor rendimiento.     

Para comenzar con esta metodología, lo primero que vamos a hablar es sobre el:
**CONJUNTO DE DATOS** 

**Ejemplo:** 

	Queremos resolver el problema de la clasificación de una transacción bancaria 

Lo primero que haremos, si vamos a utilizar una técnica de #machine_learning basada en #aprendizajeSupervisado, es recopilar un conjunto de transacciones pasadas, de estas extraer una serie de atributos o características de entrada y también clasificarlas como fraudulentas o legítimas.  #Regresión_logística (los valores de los datos son discretos, rango acotado de valores)

Ver el conjunto de datos en el slide, vemos las **características de entrada** como por ejemplo el tiempo que llevaba esa cuenta abierta en días, el número de elementos, hora local cuando se realizó esa transferencia, método de pago, y por último la **variable Y** que básicamente nos da la etiqueta de estas transacciones diciendo que la misma es **legítima representada con un 0**, o **fraudulenta representada con un 1**. 

**Tabla de 2 dimensiones:** 
Donde por un lado tendremos cada una de las transacciones que hemos recopilado del pasado (cada fila sería, la t1, t2, t3, transacción 4 y así...), en las columnas tendremos los atributos de entrada (o sea las características de entrada que extraemos de esas transacciones) y también tendremos la etiqueta o atributo de salida que es la variable Y y nos dice si esa transacción es legítima o no. 

|     |                |          |           |            |                    |
| --- | -------------- | -------- | --------- | ---------- | ------------------ |
|     | accountAgeDays | numItems | localTime | payMethod  | Variable Y (label) |
| t1  | 29             | 1        | 4.589     | MP         | 0                  |
| t2  | 26             | 1        | 4.745     | creditcard | 1                  |
| t3  | 3              | 1        | 5.035     | paypal     | 1                  |

Nuestro **objetivo:** 
Es recoger **este conjunto de datos que vemos representado con esa etiqueta, proporcionándole al algoritmo de #machine_learning** para que este sea capaz de generar esa #función/hipótesis ajustada de manera que cuando alguien realice una transacción nueva, yo haga una extracción de estos atributos sin proporcionarle la etiqueta que tenemos en nuestro conjunto de datos (variable Y), y el algoritmo sea capaz de predecirme la etiqueta, es decir, si esa transacción es legítima o fraudulenta. #Regresión_logística 

>Observar que tenemos **atributos numéricos (discretos y continuos)** como el número de días en el caso de continuo y la etiqueta de salida en el caso de valores discretos (rango de 0-1), y también **categóricos (caracteres de texto)** como por ejemplo el método de pago  

En este conjunto de datos que tengo representado, estamos recibiendo **5 características de entrada:** X1, X2, X3, X4 y X5 y una **característica de salida Y**. 

>Las **características son un atributo o grupo de atributos** que constituyen una propiedad particular o conjunto de propiedades que es único, medible y diferenciable. 

Si trato de resolver este problema mediante el uso de la #Regresión_lineal o #Regresión_logística. 

El término de regresión lineal que veíamos en regresión logística dado por:  

Siendo g la función sigmoide aplicado al término lineal theta0 + tehta1.X1 + ... 

Htheta(x) = g(theta0 + tehta1.X1 + tehta2.X2 + ... + tehta5.X5) 

>Luego utilizaremos la **variable Y** para calcular el error e ir ajustando cada uno de mis 5 parámetros de manera que tengan un valor óptimo que minimice el error y así pueda usar esa #función/hipótesis con ese valor de cada uno de los parámetros para predecir si una transacción futra es legítima o no proporcionándole al algoritmo simplemente las 5 variables de entrada que nosotros podemos extraer de esa transacción futura. 

Cada uno de los ejemplos de nuestro conjunto de datos de entrenamiento van a tener una característica X1, una característica X2, un valor para la característica X3 y así sucesivamente, o sea que las transacciones las vamos a denominar X(1), X(2), X(3) y así sucesivamente hasta X(n) donde **n = número total de ejemplos de nuestro conjunto de datos**, por lo que n se va a corresponder con el número total de transacciones que fuimos capaces de recopilar en el pasado y categorizar como legítimas o fraudulentas. 

Como vemos cada una de las transacciones tendrá un valor determinado para cada característica X (accountAgeDays, numitems, localTime, etc), o sea para la primera transacción tendremos un valor para la 1era característica X1, otro valor para la 2da característica X2 y así, lo mismo para la 2da transacción tendremos un valor para X1, un valor para X2 y así sucesivamente. 

>El número de **características de entrada lo medimos con la letra N**, es decir que, n = número de atributos o características de entrada, en este caso son 5, así que **N = 5**. 


**Conclusión:** 
Nuestro **conjunto de datos** vendrá representado por un conjunto de ejemplos que serán representativos del problema que queremos resolver (el problema que queremos resolver es que, a partir de una transferencia bancaria que realiza una persona quiero que el algoritmo de #machine_learning reciba esa transferencia y sea capaz de predecir si es legítima o no). Para resolver ese problema, recopilamos transacciones bancarias pasadas, extraigo una serie de características de entrada de estas (las 5 que vemos) y, las clasifico como fraudulentas o legítimas. 
#aprendizajeSupervisado porque etiquetamos la característica de salida Y. conjunto de datos etiqeutados. #Regresión_logística porque el rango de valores de la característica Y es acotado, valores de 0 y 1.

Así le proporcionamos este **conjunto de datos etiquetados** para que este algoritmo de #Regresión_logística **ajuste estos parámetros del modelo** Htheta(x) = g(theta0 + tehta1.X1 + tehta2.X2 + ... + tehta5.X5). 
>Y una vez que esos parámetros están ajustados, cuando recibo una transacción nueva que realiza una persona, hacemos una extracción de esas características de entrada X1 – X5, le proporcionamos estas características al algoritmo y este será capaz de predecirnos la variable de salida Y en base a esos parámetros theta1 a theta5 que ha ajustado previamente con el conjunto de datos de entrenamiento donde sabía cuál era la etiqueta de salida. 

#### Recomendaciones sobre el Conjunto de Datos a la hora de afrontar un problema real mediante el uso de técnicas de #machine_learning 

1. Disponer de una **cantidad suficiente de datos, cuantos más datos tengamos, mejor se van a comportar nuestros algoritmos de #machine_learning**, cuantos más datos tengamos menos importa el algoritmo que seleccionemos porque casi todos van a llegar a un punto de rendimiento de precisión similar, ese rendimiento será mayor a mayor cantidad de datos. 

2. Es esencial utilizar un **conjunto de datos que es representativo del problema que queremos resolver**, o sea, cuando hacemos esa extracción de las **características de entrada** debemos asegurarnos de que **extraemos aquellas que son representativas para diferenciar una transacción legítima de una que no lo es**. No sirve extraer atributos que no tienen nada que ver con el problema a resolver o que no van a diferenciar de ninguna manera una transacción legítima de una que no lo es. 

3. Los **datos tiene que ser de calidad**, de nada serviría obtener un conjunto de datos de transacciones pasadas que no son reales por lo que no podemos pretender que utilizando ese conjunto de datos artificial o inventado por alguien nos sirva para entrenar un algoritmo que haga predicciones correctas. **Tienen que ser datos del pasado reales**. 

4. Debe seleccionarse un conjunto de datos de características adecuado, minimizando el número de características irrelevantes. Cuantas más características de entrada tengamos (X1, X2, X3,) más parámetros tendrá que ajustar el algoritmo, tendrá que generar un modelo más complejo, por lo tanto, **si tenemos muchas características que son irrelevantes (o sea son significativas del problema, pero tampoco marcan mucha diferencia) puede llegar a deteriorarse el rendimiento de nuestro algoritmo**.
