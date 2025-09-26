
**Tags:**  #machine_learning #AI  #aprendizajeSupervisado #Regresión_lineal #Regresión_logística #función/hipótesis 

### Creación de un proyecto de Machine Learning 

###### **References:**
-  **Índice:** [[CURSO MACHINE LEARNING]] 
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
Además recibirán un conjunto de datos de entrenamiento (características de entrada x1---xn y una variable Y) que no tenga valores nulos, con lo cual tendremos que **aplicar transformaciones sobre ese conjunto de datos** para que todas esas variables que sean categóricas se conviertan en numéricas.

>Es decir, será necesario realizar una serie de **pre procesamiento sobre nuestro conjunto de datos** para que el algoritmo sea capaz de ingerir estos datos y de construir la #función/hipótesis 

---
#### 1. Valores perdidos
Uno de los problemas más comunes de recopilar los datos de un problema real como identificar si una transacción realizada por un cliente es fraudulenta o legítima, es que dentro de esas variables o atributos de entrada que recopilamos de cada una de las transacciones haya un **valor perdido**.

ya sabemos que en el conjunto de datos tenemos:
- Características de entrada X1, X2, X3,..., Xn
- Característica de salida Y (label 0 o 1)

A veces no tendremos valores de ciertas características de entrada, por ejemplo un dato perdido de la característica de entrada X3 de la transacción número 5

>valor de característica de entrada X3 de la fila (transacción) 5 = Valor perdido = NULL

>Tendremos un problema con esto porque nuestro algoritmo de #machine_learning no será capaz de ingerir datos con valores vacíos (NULL)
>
   Por eso tenemos que **transformar el conjunto de datos** para evitar esto.

La forma más común de **deshacernos de esos valores perdidos o nulos** suelen ser 3 formas:
1. Eliminar el ejemplo del conjunto de datos 

2. Eliminar la característica (feature) de entrada que sé que tiene varios valores nulos porque fueron datos difíciles de recuperar, entonces no podemos eliminar tantos ejemplos porque sino nos quedaríamos sin datos, entonces más fácil en ese caso sería eliminar la característica de entrada X.

3. Podemos asignarle un valor determinado, por ejemplo asignándole como valor una media aritmética de todos los valores de esa característica. Por ejemplo, si me falta un valor de entrada X5 para la transacción 3, sumo todos los valores de esa característica X5 y divido por el número total de ejemplos y así obtengo el valor de la media aritmética. Es decir, sustituir el NULL con la media o la mediana o con algún otro tipo de medida matemática
---
#### 2. Características categóricas
Estos se corresponden a valores categóricos.
La mayoría de los algoritmos de #machine_learning requieren valores numéricos para funcionar, por lo que necesitamos **transformar estas variables categóricas en números**

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
A veces tenemos características X que tienen ejemplos con valores muy grandes y otros ejemplos con valores muy pequeños. Es decir, valores muy dispares, valores a diferentes escalas.

Los algoritmos de #machine_learning  no funciones bien cuando los valores están muy dispares.

Tenemos que hacer que no tengan valores tan diferentes pero que conserven la distribución de datos que tenía el conjunto original. Por lo tanto tengo que buscar la manera de escalar los datos.

**Existen 2 Mecanismos principales:**
1. Min-max scaling (normalización)
2. Estandarización

min 14.30










