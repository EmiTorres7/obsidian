
**Tags:**  #machine_learning #AI  #aprendizajeSupervisado #Regresión_lineal #Regresión_logística #función/hipótesis 

### Creación de un proyecto de Machine Learning 

###### **References:**
- **Índice:** [[CURSO MACHINE LEARNING]] 
- **Link:** [Notebook Visualización_de_datos](http://localhost:8888/notebooks/6_Visualizaci%C3%B3n+del+conjunto+de+datos.ipynb#Buscando-correlaciones)

- [[Qué es Machine Learning]]
- [[Qué es Machine Learning#Sección 5 - Clasificación de los sistemas de Machine Learning]]
- [[Qué es Machine Learning#**Aprendizaje Supervisado** aprendizajeSupervisado]]
---
### Pre-procesamiento del conjunto de datos
**Problemas que nos encontramos en el conjunto de datos:**
[[#1. Valores perdidos]]
[[#2. Características categóricas]]
[[#3. Escalado y estandarización de características]]


>Otro paso importante es la **Preparación de los valores de cada una de las características de entrada de nuestro conjunto de datos**

Cuando tratamos de afrontar un problema real y recopilar datos de ese problema como la detección de una transacción bancaria fraudulenta, tenemos un conjunto de datos con valores para cada una de las características de diferentes tipos (valores numéricos discretos, continuos, valores categóricos, etc).

Sin embargo, los algoritmos de #machine_learning en la mayoría de los casos van a recibir valores únicamente numéricos.

Además recibirán un conjunto de datos de entrenamiento (características de entrada x1---xn y una variable Y) que **no tenga valores nulos**, con lo cual tendremos que **aplicar transformaciones sobre ese conjunto de datos** para que todas esas **variables que sean categóricas se conviertan en numéricas**.

>Es decir, será necesario realizar una serie de **pre procesamiento sobre nuestro conjunto de datos** para que el algoritmo sea capaz de ingerir estos datos y de construir la #función/hipótesis 

---
#### 1. Valores perdidos
[[#Pre-procesamiento del conjunto de datos]]
Uno de los problemas más comunes de recopilar los datos de un problema real como identificar si una transacción realizada por un cliente es fraudulenta o legítima, es que dentro de esas variables o atributos de entrada que recopilamos de cada una de las transacciones **haya un** **valor perdido**.

ya sabemos que en el conjunto de datos tenemos:
- Características de entrada X1, X2, X3,..., Xn
- Característica de salida Y (label 0 o 1)

A veces no tendremos valores de ciertas características de entrada, por ejemplo un dato perdido de la característica de entrada X3 de la transacción número 5

>valor de característica de entrada X3 de la fila (transacción) 5 = Valor perdido = NULL

>Tendremos un problema con esto porque nuestro algoritmo de #machine_learning no será capaz de ingerir datos con valores vacíos (NULL)
>
   Por eso tenemos que **transformar el conjunto de datos** para evitar esto.

>La forma más común de **deshacernos de esos valores perdidos o nulos** suelen ser 3 formas:
1. Eliminar el ejemplo del conjunto de datos 

2. Eliminar la característica (feature) de entrada que sé que tiene varios valores nulos porque fueron datos difíciles de recuperar, entonces no podemos eliminar tantos ejemplos porque sino nos quedaríamos sin datos, entonces más fácil en ese caso sería eliminar la característica de entrada X.

3. Podemos asignarle un valor determinado, por ejemplo asignándole como valor una media aritmética de todos los valores de esa característica. Por ejemplo, si me falta un valor de entrada X5 para la transacción 3, sumo todos los valores de esa característica X5 y divido por el número total de ejemplos y así obtengo el valor de la media aritmética. Es decir, sustituir el NULL con la media o la mediana o con algún otro tipo de medida matemática
---
#### 2. Características categóricas
[[#Pre-procesamiento del conjunto de datos]]
Estos se corresponden a valores categóricos.

>La mayoría de los algoritmos de #machine_learning requieren valores numéricos para funcionar, por lo que necesitamos **transformar estas variables categóricas en números**

El mecanismo más común que se conoce para hacer esto: **codificación o encoding** -> 

#One-Hot_Encoding
>Este mecanismo va a utilizar un array de bits con tantos bits como valores diferentes tiene la característica categórica y después va a poner como positivo 1 bit por cada una de esas categorías

**EJEMPLO**
SI tengo 4 formas de pago para una característica de entrada X4, vamos a seleccionar un array de 4 bits y tendríamos:

Paypal = [1,0,0,0]
credicard = [0,1,0,0]
MP = [0,0,1,0]

Por lo tanto ya no serán valores categóricos, sino este vector numérico.

#Dummy_Coding
Esto reduce el grado de libertad utilizando k - 1 nuevas características. Siendo K el número de posibles valores distintos para la característica categórica.

siendo k = 3
paypal = [1,0]
credicard = [0,1]
other = [0,0]

---
#### 3. Escalado y estandarización de características
[[#Pre-procesamiento del conjunto de datos]]
A veces tenemos características X que tienen ejemplos con valores muy grandes y otros ejemplos con valores muy pequeños. Es decir, valores muy dispares, valores a diferentes escalas.

Los algoritmos de #machine_learning  no funciones bien cuando los valores están muy dispares.

Tenemos que hacer que no tengan valores tan diferentes pero que conserven la distribución de datos que tenía el conjunto original. Por lo tanto tengo que buscar la manera de escalar los datos.

###### **Existen 2 Mecanismos principales:**
**1. Min-max scaling (normalización)**
Nos referimos a escalar los valores de las características numéricas en un rango entre 0 y 1.
Si escalamos los valores de un atributo que tiene valores muy dispares como:
	28.20469
	0.010000
	0.002777

Luego de normalizar tenemos los sgtes valores en un rango entre 0 y 1:
	0.9
	0.0
	0.1

De esta forma, mantiene un poco la distribución o la escala de los datos anteriores, y redujo los valores anteriores para que no tengan escalas tan diferentes.

Se calcula restando el valor mínimo y dividiendo por el máximo menos el mínimo
	n - min / max - min


**2. Estandarización**
Se refiere a cambiar la distribución de cada característica para que tenga una media de 0 y una DS de 1. 
Básicamente al igual que el caso anterior, reduce la escala y mantener todas esas características que se encontraban con valores muy dispares en un rango similar, pero a diferencia del anterior, no los va a limitar en un rango entre 0 y 1.

Los va a limitar en rangos bastante similares.

Se calcula restando el valor medio y dividiendo el resultado por el DS
	n - valor medio / DS

Luego de aplicar normalización, los valores de la característica de entrada de arriba son los sgtes:
	5.3
	0.0
	0.5
	
Mantiene esas proporciones y distribución de mi conjunto de datos original, pero nos escala los valores de manera que ahora se encuentran todos en un rango más pequeño y la diferencia de las escalas de sus valores no son tan grandes como en el conjunto de datos inicial

---
### Desequilibrio de los datos
[[#Pre-procesamiento del conjunto de datos]]
Otro de los problemas más comunes con los que nos podemos encontrar cuando estamos tratando con un conjunto de datos real aplicando técnicas de aprendizaje automático.

Ocurre mucho en diferentes disciplinas cuando tratamos de aplicar #machine_learning a diferentes problemas reales, por ejemplo:

- **ciberseguridad o seguridad de la información**,
Si queremos determinar si una transacción es fraudulenta o legítima, dispondremos de un conjunto de datos con muchos ejemplos negativos, es decir, con muchas transacciones legítimas y muy poquitos ejemplos positivos (o sea, muy pocas transacciones fraudulentas)-

Esto es porque lo más normal es que las personas realicen transacciones bancarias legítimas y muy de vez en cuando haya una transacción fraudulenta, entonces esa diferencia se va a ver reflejado en nuestro conjunto de datos de entrenamiento, por lo tanto estará formado por muchos ejemplos legítimos y pocos ejemplos fraudulentos.

De esta forma, los ejemplos positivos tendrán más influencia en los datos porque son más cantidad, entonces la #función/hipótesis no se adapta muy bien a esos ejemplos fraudulentos y, en consecuencia, no será capaz de predecir correctamente.

Por lo tanto, cuando tenemos datos muy desequilibrados tendremos que aplicar alguna técnica para tratar de equilibrarlos:

1. **Repetir los ejemplos de casos fraudulentos**, o sea al tener pocos de estos los voy a duplicar de manera de ahora tener el doble de ejemplos que tenía originalmente (aunque muchos de ellos serán iguales, habrá 2 ejemplos iguales dentro de ese conjunto de datos de entrenamiento). **Esto se denomina #oversample**

2. **Seleccionar un subconjunto de la clase mayoritaria**, por ejemplo si tenemos un 90% de datos legítimos y un 10% de datos fraudulentos, lo que hacemos es recoger ese 90% y reducirlo a la mitad. **Esto se denomina #undersample**

3. **Modificar la función de error**, no se suele usar mucho, de esta forma cada ejemplo de la clase minoritaria tenga más influencia en el modelo.







