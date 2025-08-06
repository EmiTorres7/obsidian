2025-07-30 15:26

**Tags:** #machine_learning  #AI #aprendizajeSupervisado #función/hipótesis 

### Creación de un proyecto de Machine Learning 

###### **References:**
-  **Índice:** [[CURSO MACHINE LEARNING]] 
- [[Qué es Machine Learning]]
- [[Qué es Machine Learning#Sección 5 - Clasificación de los sistemas de Machine Learning]]
- [[Qué es Machine Learning#**Aprendizaje Supervisado** aprendizajeSupervisado]]

----
#### VISUALIZACIÓN DEL CONJUNTO DE DATOS 

Vimos que el **conjunto de datos** está formado por: 

-  Conjunto de **características de entrada** 

- **Una característica de salida** que se corresponde con ese valor que nosotros queremos predecir en el futuro. 

- Un conjunto de ejemplos: **conjunto de datos** 

**Problema:** resolver si una transacción es legítima o fraudulenta. 

>En esta sección: Seguiremos profundizando en el concepto de conjunto de datos y vamos a ver diferentes **funciones y librerías útiles** para poder **leer el conjunto de datos** que se encuentra en diferentes formatos y también, para poder **visualizarlo** y ganar intuiciones sobre los datos que se encuentren dentro de ese conjunto. 

**Conjunto de datos conocido como NSL-KDD**: 
Este conjunto de datos sirve para clasificar tráfico de red en:
- anómalo o malicioso y, 
- normal.  

Es un conjunto de **datos real**. Formado mediante la captura de tráfico de red real 

>Para formarlo:
>Han capturado tráfico de **paquetes de red que han agrupado en flujos** (un flujo no es más que un conjunto de paquetes de red que pueden determinar por ejemplo una conexión o una sesión, pero básicamente es una **agrupación de paquetes de red**), lo que hicieron fue generar tráfico de red malicioso, generar tráfico de red normal o legítimo, y han capturado ese tráfico de red, lo agruparon en flujos.
>
>Cada una de las **filas** de nuestro conjunto de datos es un **flujo de tráfico de red**, y han **clasificado cada una de las filas (cada uno de los flujos) como anómalo o normal** en función de si ese tráfico de redes se había producido como consecuencia de actividad maliciosa o si ese tráfico de red se había producido como consecuencia de actividad normal o legítima. 

>Por lo tanto, en este caso tendremos un **conjunto de datos de tráfico de red (concretamente flujos)** clasificados como **normales o anómalos** 

>Nuestro **objetivo** será entrenar este conjunto de datos de manera que pueda poner este algoritmo analizando tráfico de red y sea capaz de identificar cuando el tráfico de red sea malicioso y cuando no. 


**Comentario:** 
Este **conjunto de datos suele utilizarse de manera muy frecuente para evaluar herramientas IDS basadas en red** (es decir, herramientas de detección de intrusiones de red). Podemos usar este conjunto de datos para evaluar una herramienta de detección de intrusiones en red. En este caso lo vamos a **utilizar para construir un modelo de aprendizaje automático**. #machine_learning  

##### **Ficheros de datos**: 

El conjunto de datos vendrá formado básicamente por los ficheros que encontramos ahí, a nosotros nos va a interesar los 2 primeros ficheros (KDDTrain + ARFF y KDDTrain + TXT).  

- **KDDTrain+.ARFF**: The full NSL-KDD train set with binary labels in ARFF format
- **KDDTrain+.TXT**: The full NSL-KDD train set including attack-type labels and difficulty level in CSV format

Estos **2 ficheros se corresponden con el subconjunto de datos de entrenamiento**, hoy no conocemos lo que es el #train_set (**conjunto de datos de entrenamiento**) pero lo sabremos en cuanto avancemos un poco en este tema, concretamente en la siguiente sección veremos en qué consisten estos conjuntos de datos o subconjuntos de entrenamiento, de validación y de pruebas, y por qué tiene sentido partir nuestro conjunto de datos de entrenamiento. 

> conjunto de datos o subconjuntos de datos de entrenamiento, de validación y de pruebas

- Es el **mismo conjunto de datos**, pero representado en **diferentes formatos**, **.ARFF** y **.TXT** (en concreto en **formato .CSV)** 

- El **formato CSV** es el más utilizado para almacenar en disco conjunto de datos y básicamente se forma de la siguiente manera: 

1. Tendremos un **conjunto de características de entrada** (valores que estarán en la primera fila del fichero) donde estos valores o nombres de las características de entrada estarán separados entre comas, 
2. Luego tendremos **diferentes filas con cada uno de los valores para cada una de las características de entrada de cada uno de los ejemplos** y cada uno de estos valores también estarán separados entre comas. 


Por ahora vamos a quedarnos que esto que vemos aquí es **nuestro conjunto de datos completo** (nuestro conjunto de datos en el que tenemos ese **tráfico de red clasificado como anómalo y legítimo**) 

#### Lectura de Conjunto de Datos 

>Si quiero **leer este conjunto de datos** (que puedo hacerlo en los 2 formatos) lo puedo hacer usando diferentes funciones, por ejemplo, puedo usar las **funciones que vienen implementadas por defecto en #Python**. 

Puedo utilizar la **función típica de lectura de un fichero y leer las líneas del fichero TXT para ver cómo me lo representa**.  
Si ejecutamos esto vemos que nos lo representa como una **lista de cadenas de texto**, vemos las cadenas de texto entre ‘ ‘ y cada una de ellas agrupadas dentro de una lista. 

```
['0,tcp,ftp_data,SF,491,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,2,2,0.00,0.00,0.00,0.00,1.00,0.00,0.00,150,25,0.17,0.03,0.17,0.00,0.00,0.00,0.05,0.00,normal,20\n',
'0,udp,other,SF,146,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,13,1,0.00,0.00,0.00,0.00,0.08,0.15,0.00,255,1,0.00,0.60,0.88,0.00,0.00,0.00,0.00,0.00,normal,15\n',> '0,tcp,http,SF,229,934,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,3,3,0.00,0.00,0.00,0.00,1.00,0.00,0.00,5,255,1.00,0.00,0.20,0.05,0.00,0.01,0.00,0.00,normal,21\n',
...]
````

**Cada una de las cadenas de texto se corresponden con una línea del fichero** como podemos observar el salto de línea con el /n. 

>Estas líneas básicamente tienen los **valores de cada una de las características de entrada (x1, x2, x3...) separados entre comas**. 

>Es decir, el **primero (primer flujo de tráfico de red)** ‘0, tcp, ftp_data,  ‘ será el primero flujo de trafico de red y cada uno de esos serán los valores para las características de entrada X1=0, X2=tcp, X3=tp_data, etc.. 

Después tendremos el **2do flujo de tráfico de red** de mi conjunto de datos con sus valores para cada característica de entrada. 

> Como podemos ver es una manera poco útil de representar nuestro conjunto de datos. 

>Por lo tanto, en lugar de usar las funciones que vienen implementadas por defecto en #Python, **vamos a utilizar #pandas para leer nuestro conjunto de datos**. Este ya tiene implementada una **función por defecto** que es capaz de leer **fichero txt** o en otro formato que vengan como **CSV**. 

	La función es **read_csv()** 

```python
import pandas as pd

df = pd.read_csv("datasets/NSL-KDD/KDDTrain+.txt")
df
```


>Si **leemos el conjunto de datos** con #pandas, esta función nos lo representa de una forma más linda, nos muestra el número de rows (es decir, el número de flujos que sería 125mil) y 43 columnas 
	 **125972 rows (número de flujos) × 43 columns**
 por lo que nos dice que tenemos 42 características de entrada (X) y 1 característica de salida(Y). 

Como el **conjunto de datos no trae los nombres de las características de entrada**, lo que hace #pandas es considerar que la primera fila con los valores de las características de entrada son los nombres de estas, pero estos no son los nombres sino los valores para cada una de las características de entrada X1, X2,..., Xn del primer flujo o el primer ejemplo de nuestro conjunto de datos. 

>Por lo tanto, en el TXT en **formato CSV no trae los nombres de las características de entrada**. 

Mostramos los ficheros en el directorio del conjunto de datos 

Por lo tanto, **vamos a listar nuestro directorio de conjunto de datos ya vamos a ver si podemos leerlo en algún otro formato que traiga los nombres de los atributos de entrada** (características de entrada X). 

```python
Import os 

os.listdir(“NSL-KDD/”) 

```

Al ejecutar esto vemos que tenemos un KDDTest+.arff.:

['index.html',
 'KDDTest+.arff',
 'KDDTest+.txt',
 'KDDTest-21.arff',
 'KDDTest-21.txt',
 'KDDTest1.jpg',
 'KDDTrain+.arff',
 'KDDTrain+.arff~',
 'KDDTrain+.txt',
 'KDDTrain+_20Percent.arff',
 'KDDTrain+_20Percent.txt',
 'KDDTrain1.jpg']
 
>Esta **extensión .arff** (Atribute-Relation Fil Format) se trata de un **archivo de formato ASCII** que lo que **describe es una lista de instancias**, es decir, un conjunto de datos con atributos. 

Instalamos nuevo paquete en el kernel de jupyter notebook para parsear archivos arff 

>Si buscamos una función dentro de #pandas para **leer archivos .arff** vamos a darnos cuenta de que **no existe ninguna función de ese estilo**, por lo que necesitaremos **instalar un nuevo paquete de #python que nos permita hacer esto**. 

	el paquete **liac-arff**: nos permite leer archivos .arff

```python
#Instalamos el paquete liac-arff: nos permite leer archivos .arff 

Import sys 

1{sys.executable} -m pip install liac-arff 

#Luego de instalamos, lo importamos para utilizarlo 

Import arrf 
````

Vamos a utilizar el método de #python open() para abrir el archivo .arff que tenemos en nuestro conjunto de datos. 

>Luego vamos a usar una función de la **librería arff**, la función es **arff-load()** para cargarlo e interpretar sus valores. 

```python
# Lectura del conjunto de datos que se encuentra en formato .arff
import arff

with open('datasets/NSL-KDD/KDDTrain+.arff', 'r') as train_set:
    df = arff.load(train_set)

df.keys()
```

minuto 13.09
>Al ejecutar esto y leemos este fichero arff, nos dice que el resultado de leerlo con esta librería es un **diccionario que tiene claves**, de las que contiene a nosotros **nos van a interesar 2**. 

>Dict_keys([‘description’, ‘relation’, ’attributes’, ‘data’]) 

1. Una será la **clave ‘data’** que representa los datos, es decir cada uno de los valores de las características de entrada de mi conjunto de datos. 

2. Por otro lado, la **clave ‘attributes’** que tiene el nombre de los atributos de cada una de las características de entrada. 


Me muestra todas las claves df.keys()  

Con df[“data”] me muestra todos los valores de las características de entrada 

Con df[“attributes”] me muestra el nombre de cada una de las características de entrada (x1, X2, x3, etc), además nos dice si se considera un valor REAL, valor numérico, si es un valor categórico nos muestra qué categorías tiene como tcp, udp e icmp, esta característica de entrada recopila el tipo de protocolo utilizado. 

#Parseamos los atributos para obtener únicamente los nombres 

14.20
