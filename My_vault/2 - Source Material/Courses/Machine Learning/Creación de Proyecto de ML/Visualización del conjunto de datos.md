2025-07-30 15:26

**Tags:** #machine_learning  #AI #aprendizajeSupervisado #función/hipótesis 

### Creación de un proyecto de Machine Learning 

###### **References:**
**Link:** [Notebook Visualización_de_datos](http://localhost:8888/notebooks/6_Visualizaci%C3%B3n+del+conjunto+de+datos.ipynb#Buscando-correlaciones)
-  **Índice:** [[CURSO MACHINE LEARNING]] 
- [[Qué es Machine Learning]]
- [[Qué es Machine Learning#Sección 5 - Clasificación de los sistemas de Machine Learning]]
- [[Qué es Machine Learning#**Aprendizaje Supervisado** aprendizajeSupervisado]]

----
#### VISUALIZACIÓN DEL CONJUNTO DE DATOS 
[[#1. Lectura del conjunto de datos]]
- [[#**Ficheros de datos**]]
- [[#Lectura de Conjunto de Datos]]
[[#2. Funciones básicas de visualización de los datos]]
[[#3. Funciones avanzadas de visualización de los datos]]

---
## 1. Lectura del conjunto de datos

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


>Al ejecutar esto y leemos este **fichero arff**, nos dice que el resultado de leerlo con esta librería es un **diccionario que tiene claves**, de las que contiene a nosotros **nos van a interesar 2**. 

>Dict_keys([‘description’, ‘relation’, ’attributes’, ‘data’]) 

1. Una será la **clave ‘data’** que representa los datos, es decir cada uno de los valores de las características de entrada de mi conjunto de datos. 

2. Por otro lado, la **clave ‘attributes’** que tiene el nombre de los atributos de cada una de las características de entrada. 
```python
df["data"]

#consola Con df[“data”] me muestra todos los valores de las características de entrada 
[[0.0,
  'tcp',
  'ftp_data',
  'SF',
  491.0,
  0.0,
  '0',..]
  
df["attributes"]

#consola: Con df[“attributes”] me muestra el nombre de cada una de las características de entrada (x1, X2, x3, etc), además nos dice si se considera un valor REAL, valor numérico, si es un valor categórico nos muestra qué categorías tiene como tcp, udp e icmp, esta característica de entrada recopila el tipo de protocolo utilizado. 

[('duration', 'REAL'),
 ('protocol_type', ['tcp', 'udp', 'icmp']),
 ('service',
  ['aol',
   'auth',
   'bgp',
   'courier',
   'csnet_ns',
```

Vamos a quedarnos con el nombre de los atributos
```python
# Parseamos los atributos para obtener únicamente los nombres
atributos = [attr[0] for attr in df["attributes"]]
atributos
```

Me muestra todas las claves df.keys()  
Una vez que tenemos los nombres de los atributos y, tenemos además, los datos, vamos a transformarlos en un #data_frame de #pandas
```python
# Leemos el conjunto de datos con Pandas para facilitar la manipulación
df = pd.DataFrame(df["data"], columns=atributos)
df
#125973 rows × 42 columns
```
Esto lo hacemos porque #pandas nos representa los datos de una manera más bonita y nos permite aplicar transformaciones de una manera más sencilla que usando estructuras propias de #Python 
Entonces le paso los datos ["data"] y le digo que las columnas sean igual a los nombres de las columnas de los atributos X1, X2, Xn e Y, serán igual a los nombres que tenemos en la lista atributos (**columns=atributos**) luego de haber parseado los atributos para obtener los nombres (**atributos = [attr[0] for attr in df["attributes"]]**).

Entonces luego de ejecutar este código, hace esta lectura del df y vemos un conjunto de datos en 2 dimensiones bien representado:

| duration | protocol_type | service | flag     | src_bytes | dst_bytes | land   | wrong_fragment | urgent | hot | ... | dst_host_srv_count | dst_host_same_srv_rate | dst_host_diff_srv_rate | dst_host_same_src_port_rate | dst_host_srv_diff_host_rate | dst_host_serror_rate | dst_host_srv_serror_rate | dst_host_rerror_rate | dst_host_srv_rerror_rate | class |         |
| -------- | ------------- | ------- | -------- | --------- | --------- | ------ | -------------- | ------ | --- | --- | ------------------ | ---------------------- | ---------------------- | --------------------------- | --------------------------- | -------------------- | ------------------------ | -------------------- | ------------------------ | ----- | ------- |
| 0        | 0.0           | tcp     | ftp_data | SF        | 491.0     | 0.0    | 0              | 0.0    | 0.0 | 0.0 | ...                | 25.0                   | 0.17                   | 0.03                        | 0.17                        | 0.00                 | 0.00                     | 0.00                 | 0.05                     | 0.00  | normal  |
| 1        | 0.0           | udp     | other    | SF        | 146.0     | 0.0    | 0              | 0.0    | 0.0 | 0.0 | ...                | 1.0                    | 0.00                   | 0.60                        | 0.88                        | 0.00                 | 0.00                     | 0.00                 | 0.00                     | 0.00  | normal  |
| 2        | 0.0           | tcp     | private  | S0        | 0.0       | 0.0    | 0              | 0.0    | 0.0 | 0.0 | ...                | 26.0                   | 0.10                   | 0.05                        | 0.00                        | 0.00                 | 1.00                     | 1.00                 | 0.00                     | 0.00  | anomaly |
| 3        | 0.0           | tcp     | http     | SF        | 232.0     | 8153.0 | 0              | 0.0    | 0.0 | 0.0 | ...                | 255.0                  | 1.00                   | 0.00                        | 0.03                        | 0.04                 | 0.03                     | 0.01                 | 0.00                     | 0.01  | normal  |
| 4        | 0.0           | tcp     | http     | SF        | 199.0     | 420.0  | 0              | 0.0    | 0.0 | 0.0 | ...                | 255.0                  | 1.00                   |                             |                             |                      |                          |                      |                          |       |         |

**filas:** representan cada uno de los ejemplos de mi conjunto de datos (cada flujo de tráfico de red)
(125973 rows)
**columnas:** cada una de las columnas representan cada una de las características, es decir, las características o atributos de entrada que extrajimos de cada uno de los flujos de tráfico de red.
(42 columns)

*Columnas/Atributos*: Básicamente lo que se ha extraído es la duración, el tipo de protocolo utilizado, el servicio utilizado, los flags que tenía, el número de bytes de origen, número de bytes de destino. Concretamente tenemos 42 características
- 41 características de entrada (x)
- 1 característica de salida (Y): nos dice si ese flujo representado por cada una de las filas de mi conjunto de datos de mi #data_frame es un flujo normal o es un flujo anómalo

La última característica se corresponde con la **clase**

>Llegados a este punto lo ideal es construir una función que permita leer el conjunto de datos de manera más limpia. Este tipo de prácticas son de gran utilidad para que nuestro código en el Jupyter Notebook sea más modular y pueda reutilizarse de manera más sencilla para futuros ejercicios.

>**Resumen:** Ya hemos investigado en qué consistía ese formato .arff, cómo parsear ese fichero y extraer los atributos, etc, de manera que esto nos sirve en el caso que tengamos alguna vez un archivo con este formato .arff. 
>Por lo tanto, definimos una función que nos parsea ese fichero .arff de manera automática. de esta forma si quiero parsearlo en el futuro, lo único que haremos será llamar a esa función, pasarle dónde se encuentra el fichero .arff, y automáticamente lo que hace es leerlo, lo transforma e incluso, me lo convierte a un #data_frame de #pandas, me devuelve ya el df de pandas con los nombres de los atributos de cada una de las columnas y todos los ejemplos de tráfico de red en cada una de las filas 

```python
def load_kdd_dataset(data_path):
    """Lectura del conjunto de datos NSL-KDD."""
    with open(data_path, 'r') as train_set:
        dataset = arff.load(train_set)
    attributes = [attr[0] for attr in dataset["attributes"]]
    return pd.DataFrame(dataset["data"], columns=attributes)
```

---
## 2. Funciones básicas de visualización de los datos
[[#VISUALIZACIÓN DEL CONJUNTO DE DATOS]]

>Una vez que tenemos leídos los datos, es importante visualizar esos datos. Ganar intuición sobre qué datos hay exactamente, en este caso sabemos que estos datos son flujos de tráfico de red que están categorizados como legítimos o anómalos #aprendizajeSupervisado  
>
>Pero, ¿Cuántos flujos hay clasificados como anómalos y como legítimos?, ¿ hay valores categóricos dentro de esos atributos de entrada?, ¿hay valores perdidos o nulos?
>
>Para esto vamos a visualizar nuestro conjunto de datos.

* El **proceso de visualización** siempre debe **realizarse** sobre el **trainning_set** y **apartando el test set**. 
Esto evita que nuestro cerebro genere intuiciones del test set que podemos incorporar en nuestro modelo y que pueden provocar una especie de sobre entrenamiento y que no generalice bien para nuevos ejemplos

* Una buena práctica es **crear una copia del trainning set** y jugar con ella. De esta manera, si realizamos transformaciones que dañan el tranning set, el original no se ve afectado

```python
# Lectura y copia del conjunto de datos
df_orig = load_kdd_dataset('datasets/NSL-KDD/KDDTrain+.arff') #leemos el cjto de datos
df = df_orig.copy() #realizamos una copia

# Mostrar en pantalla un número determinado de filas
df.head(10)

# Mostrar información básica sobre el conjunto de datos
df.info()
```

>De esta manera podemos tener una visión global de exactamente qué es cada una de las características 

	df.head(10)

| duration | protocol_type | service | flag       | src_bytes | dst_bytes | land   | wrong_fragment | urgent | hot | ... | dst_host_srv_count | dst_host_same_srv_rate | dst_host_diff_srv_rate | dst_host_same_src_port_rate | dst_host_srv_diff_host_rate | dst_host_serror_rate | dst_host_srv_serror_rate | dst_host_rerror_rate | dst_host_srv_rerror_rate | class |         |
| -------- | ------------- | ------- | ---------- | --------- | --------- | ------ | -------------- | ------ | --- | --- | ------------------ | ---------------------- | ---------------------- | --------------------------- | --------------------------- | -------------------- | ------------------------ | -------------------- | ------------------------ | ----- | ------- |
| 0        | 0.0           | tcp     | ftp_data   | SF        | 491.0     | 0.0    | 0              | 0.0    | 0.0 | 0.0 | ...                | 25.0                   | 0.17                   | 0.03                        | 0.17                        | 0.00                 | 0.00                     | 0.00                 | 0.05                     | 0.00  | normal  |
| 1        | 0.0           | udp     | other      | SF        | 146.0     | 0.0    | 0              | 0.0    | 0.0 | 0.0 | ...                | 1.0                    | 0.00                   | 0.60                        | 0.88                        | 0.00                 | 0.00                     | 0.00                 | 0.00                     | 0.00  | normal  |
| 2        | 0.0           | tcp     | private    | S0        | 0.0       | 0.0    | 0              | 0.0    | 0.0 | 0.0 | ...                | 26.0                   | 0.10                   | 0.05                        | 0.00                        | 0.00                 | 1.00                     | 1.00                 | 0.00                     | 0.00  | anomaly |
| 3        | 0.0           | tcp     | http       | SF        | 232.0     | 8153.0 | 0              | 0.0    | 0.0 | 0.0 | ...                | 255.0                  | 1.00                   | 0.00                        | 0.03                        | 0.04                 | 0.03                     | 0.01                 | 0.00                     | 0.01  | normal  |
| 4        | 0.0           | tcp     | http       | SF        | 199.0     | 420.0  | 0              | 0.0    | 0.0 | 0.0 | ...                | 255.0                  | 1.00                   | 0.00                        | 0.00                        | 0.00                 | 0.00                     | 0.00                 | 0.00                     | 0.00  | normal  |
| 5        | 0.0           | tcp     | private    | REJ       | 0.0       | 0.0    | 0              | 0.0    | 0.0 | 0.0 | ...                | 19.0                   | 0.07                   | 0.07                        | 0.00                        | 0.00                 | 0.00                     | 0.00                 | 1.00                     | 1.00  | anomaly |
| 6        | 0.0           | tcp     | private    | S0        | 0.0       | 0.0    | 0              | 0.0    | 0.0 | 0.0 | ...                | 9.0                    | 0.04                   | 0.05                        | 0.00                        | 0.00                 | 1.00                     | 1.00                 | 0.00                     | 0.00  | anomaly |
| 7        | 0.0           | tcp     | private    | S0        | 0.0       | 0.0    | 0              | 0.0    | 0.0 | 0.0 | ...                | 15.0                   | 0.06                   | 0.07                        | 0.00                        | 0.00                 | 1.00                     | 1.00                 | 0.00                     | 0.00  | anomaly |
| 8        | 0.0           | tcp     | remote_job | S0        | 0.0       | 0.0    | 0              | 0.0    | 0.0 | 0.0 | ...                | 23.0                   | 0.09                   |                             |                             |                      |                          |                      |                          |       |         |

	df.info()
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 125973 entries, 0 to 125972
Data columns (total 42 columns):
 #   Column                       Non-Null Count   Dtype  
---  ------                       --------------   -----  
 0   duration                     125973 non-null  float64
 1   protocol_type                125973 non-null  object 
 2   service                      125973 non-null  object 
 3   flag                         125973 non-null  object 
 4   src_bytes                    125973 non-null  float64
 5   dst_bytes                    125973 non-null  float64
 6   land                         125973 non-null  object 
 7   wrong_fragment               125973 non-null  float64
 8   urgent                       125973 non-null  float64
 9   hot                          125973 non-null  float64

```python
# Mostrar información estadística sobre el conjunto de datos, sólo de las características numéricas, no de las categóricas.
df.describe()
```

| duration | src_bytes    | dst_bytes    | wrong_fragment | urgent        | hot           | num_failed_logins | num_compromised | root_shell    | su_attempted  | ...           | dst_host_count | dst_host_srv_count | dst_host_same_srv_rate | dst_host_diff_srv_rate | dst_host_same_src_port_rate | dst_host_srv_diff_host_rate | dst_host_serror_rate | dst_host_srv_serror_rate | dst_host_rerror_rate | dst_host_srv_rerror_rate |               |
| -------- | ------------ | ------------ | -------------- | ------------- | ------------- | ----------------- | --------------- | ------------- | ------------- | ------------- | -------------- | ------------------ | ---------------------- | ---------------------- | --------------------------- | --------------------------- | -------------------- | ------------------------ | -------------------- | ------------------------ | ------------- |
| count    | 125973.00000 | 1.259730e+05 | 1.259730e+05   | 125973.000000 | 125973.000000 | 125973.000000     | 125973.000000   | 125973.000000 | 125973.000000 | 125973.000000 | ...            | 125973.000000      | 125973.000000          | 125973.000000          | 125973.000000               | 125973.000000               | 125973.000000        | 125973.000000            | 125973.000000        | 125973.000000            | 125973.000000 |
| mean     | 287.14465    | 4.556674e+04 | 1.977911e+04   | 0.022687      | 0.000111      | 0.204409          | 0.001222        | 0.279250      | 0.001342      | 0.001103      | ...            | 182.148945         | 115.653005             | 0.521242               | 0.082951                    | 0.148379                    | 0.032542             | 0.284452                 | 0.278485             | 0.118832                 | 0.120240      |
| std      | 2604.51531   | 5.870331e+06 | 4.021269e+06   | 0.253530      | 0.014366      | 2.149968          | 0.045239        | 23.942042     | 0.036603      | 0.045154      | ...            | 99.206213          | 110.702741             | 0.448949               | 0.188922                    | 0.308997                    | 0.112564             | 0.444784                 | 0.445669             | 0.306557                 | 0.319459      |
| min      | 0.00000      | 0.000000e+00 | 0.000000e+00   | 0.000000      | 0.000000      | 0.000000          | 0.000000        | 0.000000      | 0.000000      | 0.000000      | ...            | 0.000000           | 0.000000               | 0.000000               | 0.000000                    | 0.000000                    | 0.000000             | 0.000000                 | 0.000000             | 0.000000                 | 0.000000      |
| 25%      | 0.00000      | 0.000000e+00 | 0.000000e+00   | 0.000000      | 0.000000      | 0.000000          | 0.000000        | 0.000000      | 0.000000      | 0.000000      | ...            | 82.000000          | 10.000000              | 0.050000               | 0.000000                    | 0.000000                    | 0.000000             | 0.000000                 | 0.000000             | 0.000000                 | 0.000000      |
| 50%      | 0.00000      | 4.400000e+01 | 0.000000e+00   | 0.000000      | 0.000000      | 0.000000          | 0.000000        | 0.000000      | 0.000000      | 0.000000      | ...            | 255.000000         | 63.000000              | 0.510000               | 0.020000                    | 0.000000                    | 0.000000             | 0.000000                 | 0.000000             | 0.000000                 | 0.000000      |
| 75%      | 0.00000      | 2.760000e+02 | 5.160000e+02   | 0.000000      | 0.000000      | 0.000000          | 0.000000        | 0.000000      | 0.000000      | 0.000000      | ...            | 255.000000         | 255.000000             | 1.000000               | 0.070000                    | 0.060000                    | 0.020000             | 1.000000                 | 1.000000             | 0.000000                 | 0.000000      |
| max      | 42908.00000  | 1.379964e+09 | 1.309937e+09   | 3.000000      | 3.000000      | 77.000000         | 5.000000        | 7479.000000   | 1.000000      | 2.000000      | ...            | 255.000000         | 255.000000             | 1.000000               | 1.000000                    | 1.000000                    | 1.000000             | 1.000000                 | 1.000000             | 1.000000                 | 1.000000      |

8 rows × 34 columns

```python
# Mostrar los valores únicos que tiene un atributo determinado
df["protocol_type"].value_counts()
```

Por ejemplo, yo sé que protocol_type es categórico y quiero saber cuáles son los valores que puede tomar:
- nos dice que etiquetados con el valor tcp tengo 102689 ejemplos
- con el valor udp tengo 14993 ejemplos

protocol_type
tcp     102689
udp      14993
icmp      8291
Name: count, dtype: int64

>IMPORTANTE: es útil para ver la clase: es decir, cómo están etiquetados los datos.

```python
df["class"].value_counts()
```
Nos dice que el atributo clase sólo tiene 2 valores "normal" y "anormaly", y nos dice cuántos ejemplos de flujos tengo de cada valor.

class
normal     67343  -> Tengo esta cantidad de flujos etiquetados como normales
anomaly    58630  -> Tengo esta cantidad de flujos etiquetados como anómalos
Name: count, dtype: int64

```python
# Mostrar los valores de la característica como un histograma
%matplotlib inline
import matplotlib.pyplot as plt
df["protocol_type"].hist()
```

```python
# Representar gráficamente la distribución de los atributos. Nos representará mediante histogramas, todos los atributos o características de entrada que tiene nuestro conjunto de datos o mi df de #pandas 
df.hist(bins=50, figsize=(20,15))
plt.show()
```


## 3. Funciones avanzadas de visualización de los datos
[[#VISUALIZACIÓN DEL CONJUNTO DE DATOS]]

Se  pueden utilizar funciones más avanzadas para ganar todavía más intuiciones de ese conjunto de datos que tenemos. Una de las formas de ganar más intuiciones es Buscar correlaciones entre atributos
##### Buscando correlaciones

- Se puede calcular el **coeficiente de correlación estándar** para **ver la correlación entre cada par de atributos**
- El coeficiente de correlación, solo mide **correlaciones lineales**, esto quiere decir que si x va hacia arriba, mediría si y va hacia arriba o hacia abajo.

Una correlación lineal quiere decir que si el valor de un atributo crece, el valor del otro atributo también crece en la misma proporción o disminuye en la misma proporción.
Es decir, 2 atributos están correlacionados si por ejemplo el atributo de entrada x1 crece, el atributo de entrada x2 también lo hace. O sea es cuando se produce esa correlación de que cuando uno crece o disminuye, el otro también lo hace.

- **Hay que intentar buscar correlaciones sobre todo con el atributo objetivo (el que queremeos predecir), en este caso _class_**

>Es útil medir estas correlaciones porque podemos **medir las correlaciones que hay entre nuestros atributos de entrada X1, X2, Xn y nuestra variable de salida Y**. Con lo cual nosotros vamos a saber que cuando existen correlaciones entre uno de los atributos de entrada y la variable de salida, quiere decir que ese atributo será bastante útil y que será significativo para tratar de clasificar en una categoría u otra nuestros ejemplos que tenemos en el conjunto de datos.

>También podemos usarlo para **medir la correlación que hay entre diferentes características de entrada**, de manera que si una característica de entrada sube y la otra también lo hace de la misma manera, pues a lo mejor básicamente nos están proporcionando la misma intuición, por lo que quizás no necesitaríamos las 2 características porque están muy correlacionadas, así quizás podemos eliminar una característica y dejar nuestro conjunto de datos con una característica de entrada menos lo cual exigiría menor requisitos computacionales para entrenar nuestro algoritmo de #machine_learning 


El **atributo o la etiqueta Y** de nuestro conjunto de datos es el **atributo class**

```python
#El atributo class de nuestro conjunto de datos tiene valores categoricos
df["class"]

0          normal
1          normal
2         anomaly
3          normal
4          normal
           ...   
125968    anomaly
125969     normal
125970     normal
125971    anomaly
125972     normal
Name: class, Length: 125973, dtype: object
````

Para poder **calcular la correlación:**
Vamos a transformar esos valores del atributo class de categóricos a valores numéricos.
lo que hace básicamente el código es transformar donde teníamos como valor normal lo igualará a 1 y el valor anormal lo igualará a 0
normal = 1
anormal = 0

Queremos calcular la correlación entre los atributos numéricos con la variable de salida Y

```python
from sklearn.preprocessing import LabelEncoder

# Transformamos los valores del atributo class de categoricos a numéricos
labelencoder = LabelEncoder()
df["class"] = labelencoder.fit_transform(df["class"])

# Transformamos los valores de los atributos categóricos a numéricos
df["protocol_type"] = labelencoder.fit_transform(df["protocol_type"])
df["service"] = labelencoder.fit_transform(df["service"])
df["flag"] = labelencoder.fit_transform(df["flag"])

df
```

Una vez que hemos transformado esos valores categóricos a numéricos, puedo mostrar la correlación entre los atributos de entrada de mi conjunto de datos (aquellos atributos numéricos) y mi característica de salida Y.

```python
# Mostrar la correlación entre los atributos del conjunto de datos
corr_matrix = df.corr()
corr_matrix["class"].sort_values(ascending=False)

#Me muestra la correlación que hay entre los diferentes atributos
class                          1.000000
same_srv_rate                  0.751913
dst_host_srv_count             0.722535
dst_host_same_srv_rate         0.693803
logged_in                      0.690171
flag                           0.647073
protocol_type                  0.281355
srv_diff_host_rate             0.119377
is_guest_login                 0.039279
num_access_files               0.036701
su_attempted                   0.022448
num_file_creations             0.021271
root_shell                     0.020285
hot                            0.013083
num_root                       0.011452
```

El atributo o característica clase obviamente tendrá una correlación del 100% porque es una correlación con ella misma, cuando sube una obviamente sube la otra porque es la misma característica.

Podemos ver que hay mucha correlación entre la característica de destino Y (class) y las características de entrada "same_srv_rate" (por ejemplo del 0.75), "dst_host_srv_count" con 0.72 y así podemos ver las correlaciones entre las distintas características de entrada X con la característica de salida Y.

Por lo tanto, podemos suponer que las primeras características de entrada X serán bastante útiles para clasificar los ejemplos de nuestro conjunto de datos de entrenamiento, en anómalos o en legítimos

```python
# Mostrar correlación lineal entre todos los atributos del conjunto de datos
df.corr()
```

Podemos mostrar la correlación entre todos los atributos, no únicamente con esa clase (con esa etiqueta Y) y esto lo hago con el método corr().

Así me calcula la correlación que existe entre todos los atributos que tengo en mi conjunto de datos. Nos muestra la correlación por ejemplo entre duration y procol_type o duration con service y así sucesivamente

|               | duration  | protocol_type | service   | flag      | src_bytes | dst_bytes | land      | urgent    | hot       | ...       | dst_host_srv_count | dst_host_same_srv_rate | dst_host_diff_srv_rate | dst_host_same_src_port_rate |           | dst_host_srv_diff_host_rate<br> | dst_host_serror_rate | dst_host_srv_serror_rate | dst_host_rerror_rate | dst_host_srv_rerror_rate | class     |
| ------------- | --------- | ------------- | --------- | --------- | --------- | --------- | --------- | --------- | --------- | --------- | ------------------ | ---------------------- | ---------------------- | --------------------------- | --------- | ------------------------------- | -------------------- | ------------------------ | -------------------- | ------------------------ | --------- |
| duration      | 1.000000  | 0.038241      | 0.092858  | -0.063390 | 0.070737  | 0.034878  | -0.001553 | -0.009866 | 0.003830  | 0.000705  | ...                | -0.109776              | -0.116005              | 0.254195                    | 0.228737  | -0.026669                       | -0.064948            | -0.064361                | 0.173815             | 0.199024                 | -0.048785 |
| protocol_type | 0.038241  | 1.000000      | 0.029994  | 0.093668  | -0.000974 | -0.000608 | -0.001757 | 0.169535  | -0.000965 | -0.011857 | ...                | 0.103919               | 0.001702               | 0.131380                    | -0.209105 | -0.356183                       | -0.079398            | -0.077925                | -0.015434            | -0.046938                | 0.281355  |
| service       | 0.092858  | 0.029994      | 1.000000  | -0.304014 | -0.001631 | 0.003596  | -0.009952 | 0.084404  | 0.010980  | -0.064066 | ...                | -0.407696              | -0.452696              | 0.284072                    | -0.111163 | -0.156211                       | 0.281635             | 0.277594                 | 0.150666             | 0.148405                 | -0.276548 |
| flag          | -0.063390 | 0.093668      | -0.304014 | 1.000000  | -0.008114 | -0.004096 | -0.010373 | 0.067214  | 0.005811  | 0.068437  | ...                | 0.582687               | 0.630118               | -0.283607                   | 0.195689  | 0.073773                        | -0.443441            | -0.443225                | -0.683310            | -0.718778                | 0.647073  |


Algo bastante útil de representar es lo que se llama **Matriz de Correlación**

```python
# Representar gráficamente la matriz de correlación
corr = df.corr()
fig, ax = plt.subplots(figsize=(8, 8))
ax.matshow(corr)
plt.xticks(range(len(corr.columns)), corr.columns);
plt.yticks(range(len(corr.columns)), corr.columns);
```

En el gráfico [Matriz de Correlación](http://localhost:8888/notebooks/6_Visualizaci%C3%B3n%20del%20conjunto%20de%20datos.ipynb?)
podemos ver la correlación entre todos los atributos, y observamos que cuanto más amarillo sea quiere decir que hay más correlación entre ellos 

En lugar de representar las correlaciones de todos los atributos, podemos hacerlo de un conjunto determinado de atributos: 
>attributes = ["same_srv_rate", "dst_host_srv_count", "class", "dst_host_same_srv_rate"]

```python
# Representar gráficamente las correlaciones
from pandas.plotting import scatter_matrix

attributes = ["same_srv_rate", "dst_host_srv_count", "class", "dst_host_same_srv_rate"]

scatter_matrix(df[attributes], figsize=(12,8))
plt.show()
```

En el gráfico [Matriz de Correlación](http://localhost:8888/notebooks/6_Visualizaci%C3%B3n%20del%20conjunto%20de%20datos.ipynb?)
Nos muestra en un scatter matrix (que es un formato de matriz diferente) es en qué sentido está esta correlación entre estos atributos o características de entrada que nos interesa.
Es más útil hacer esto, en lugar de representar la correlación entre todos los atributos, es más visual representar la correlación de los atributos que nosotros sospechamos que pueden tener correlación entre ellos y así representarlos gráficamente


