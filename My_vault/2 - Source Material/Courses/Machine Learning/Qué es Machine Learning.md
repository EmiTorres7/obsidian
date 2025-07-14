2025-07-09 14:13

**Tags:** #machine_learning #aprendizajeSupervisado #aprendizajeNoSupervisado 

## Machine Learning y Clasificación

###### **References:** 
- [[CURSO MACHINE LEARNING]]
- [[#Sección 5 - Clasificación de los sistemas de Machine Learning]]

- [[#1). En función de la manera en la que aprenden los algoritmos..]]
- [[#**Aprendizaje Supervisado**]]
- [[#**Aprendizaje NO Supervisado** aprendizajeNoSupervisado]]

- [[#2). En función en la manera en la que aprenden en el tiempo APRENDIZAJE ONLINE Y BATCH]]

- [[#**3). En base a la manera en que realizan las predicciones APRENDIZAJE BASADO EN INSTANCIAS Y EN MODELOS**]]
----
### Sección 5 - ¿Qué es el Machine Learning? 

Estos programas van a mejorar automáticamente a partir de la experiencia sin ser programados explícitamente. 

>**Se basa básicamente en crear un modelo y tratar de mejorarlo ajustando más datos en el modelo a lo largo del tiempo.**

Entonces nos dicen que necesitamos algo para que estos sistemas funcionen que sería por lo tanto la **experiencia** que en definitiva se va a corresponder con **datos**. 

>Nosotros vamos a **cargar estos datos** y vamos a **proporcionárselos** a algo que va a aprender automáticamente que concretamente será un **algoritmo matemático y va a construir** algo que ha denominado **modelo.** 

A partir de esos datos (de esa experiencia) crea el modelo. 

Es importante tener en cuenta este concepto, y es que **el algoritmo va ajustando algo que se denomina modelo**. 

>Cuando nosotros tenemos construido este modelo a base de ir pasándole datos (experiencia pasada), este modelo será capaz de realizar predicciones. 

**Tenemos datos (pasados, experiencia pasada) que le pasamos a un algoritmo matemático que recibe esos datos y construye un modelo, luego se ajusta ese modelo y se realizan predicciones**

#### ¿PARA QUÉ? 

Queremos ajustar un modelo que sea capaz de realizar predicciones en base a datos pasados para proporcionarle a este modelo nuevos datos y que este modelo sea capaz de realizar nuevas predicciones para esos datos que le estamos pasando. 

>Cuando hablamos de #machine_learning debemos tener en cuenta que estamos hablando de datos pasados que le proporcionamos, de un algoritmo matemático que recibe esos datos y construye un modelo y también hablamos de ajustar ese modelo y realizar predicciones. 

#### ESQUEMA 

El analista va a tratar de obtener experiencia pasada, es decir va a formar un conjunto de datos que en este caso por ej estará compuesto por correos electrónicos legítimos y correos electrónicos de spam. 

Luego de componer este conjunto de datos lo siguiente que hará es determinar un algoritmo de ML que crea que pueda ser adecuado para resolver el problema. 

El analista entonces encuentra esos datos y elige el algoritmo matemático de ML que piensa que puede resolver mejor este problema. 

Una vez que tiene esto seleccionado, el procedimiento sería el sgte.: 

**1. Entrenamiento del algoritmo** 

**2.** En base a este entrenamiento se construye el **Modelo** 

**3.** El algoritmo va ajustando una **serie de parámetros internos en base a esos datos pasados que le permite construir una especie de reglas internas** que le permiten diferenciar un correo normal de un spam. 

**4.** Una vez que eso ha terminado de ajustarse, tenemos el modelo que es capaz de realizar predicciones. 

**5.** Ese modelo lo ponemos en Evaluación, donde la vamos a pasar nuevos correos electrónicos que no estaban en el conjunto de datos que le pasamos previamente y que ha utilizado para ajustarse y determinamos si los resultados son buenos o no. 

- En caso de que no funcione, sea incorrecto, lo que hago es el análisis de los errores en donde me centro en si el conjunto de datos que he proporcionado es adecuado y en si el algoritmo matemático fue el adecuado para resolver. 
    

El analista como vemos es ajeno al motor de reglas o Modelo que realiza las predicciones y que determina si un correo electrónico es legítimo o no lo es.

##### ¿Qué pasa si el tipo de correos considerados como spam cambia a lo largo del tiempo?

Nuestras reglas o nuestro modelo para predecir esto ya no servirían si las personas que hacen correos spam empiezan a cambiar la manera en cómo detectar un correo spam, por lo tanto, nuestro modelo ya no será válido para ese nuevo tipo de correos de spam. 

Entonces, el analista tiene que extraer nuevas características que permitan diferenciar un correo normal de uno spam, tiene que ir al motor de reglas y revisar todas las reglas y ver cuáles de ellas ya no son útiles y cuáles sí lo son, y añadir las nuevas reglas que ha extraído de la fase de análisis (todo esto es un proceso lento y difícil de mantener porque es complicado adaptarse constantemente al cambio, es prácticamente imposible que el analista vaya al mismo ritmo que sus adversarios para actualizarse al cambio). 

>Sin embargo, cuando utilizamos un **enfoque basado en #machine_learning** la clave está en los datos, es decir que el analista no tiene que analizar ese motor de reglas porque él no lo ha construido, sino seleccionar un algoritmo que valía para resolver este problema y que probablemente seguirá valiendo para resolver el mismo problema. 

Ahora ese algoritmo ahora va a seguir ajustando ese modelo que ha construido, con los nuevos datos que está obteniendo de los atacantes, es decir, esos nuevos correos de spam van a formar parte de este conjunto de datos que utilizamos para entrenar, para ajustar ese modelo, utilizando ese algoritmo que ya habíamos seleccionado. Y lo único que tenemos que hacer es complementar nuestros datos de entrenamiento, volver a pasar a una fase de entrenamiento, ajustar de nuevo nuestro modelo y volver a ponerlo en producción. 

Esto no lleva casi tiempo, el recopilar esos nuevos correos de spam, introducirlos y reentrenar nuestro algoritmo sin necesidad de hacer un proceso de mantenimiento de motor de reglas. 

**¿Cuándo usar #machine_learning ?** 

- Por ejemplo, un filtro de spam, porque necesitamos reglas para diferenciarlos y además va cambiando con el tiempo.  

- Clasificación de imágenes: donde el analista no es capaz de determinar una solución a partir de información existente. 

- Tráfico de red, herramientas de seguridad que detectan amenazas, se dispone de conjunto de datos muy grandes que fluctúan o varían con mucha frecuencia. 
    

### Sección 5 - Clasificación de los sistemas de Machine Learning 
[[#Sección 5 - ¿Qué es el Machine Learning?]]

Se los podría clasificar a los algoritmos de #machine_learning en base a varios criterios, podría ser en base a la complejidad del algoritmo, en base al rendimiento, en base al tiempo de ejecución, varios criterios. 

Sin embargo, el criterio más aceptado suele ser **en base a la forma en la que aprenden**, o sea en base a la forma en la que ese modelo se va ajustando a lo largo del tiempo en base a un conjunto de datos o experiencia pasada. 

###### **1.** En función de la manera en la que se entrenan:
Es decir en la manera en la que van a ir ajustado ese modelo, acá tenemos ppalmente el **Aprendizaje Supervisado** (como el filtro de spam) y el **Aprendizaje No supervisado** y el **Aprendizaje semi-supervisado**. 

###### **2.** En función de la manera en la que aprenden en el tiempo:
O sea cómo van ajustando ese modelo a lo largo del tiempo: **Aprendizaje Online** y **aprendizaje Batch**. 

###### **3.** En función de la forma en la que realizan las predicciones:
Que serían algoritmos de aprendizaje **basados en instancias** y algoritmos de **aprendizaje basados en modelos** (este es el más frecuente). 

Un algoritmo de #machine_learning  puede ser clasificado dentro de todas estas categorías ya que en base a la manera en la que aprende puede ser u algoritmo de aprendizaje No supervisado, puede ser de tipo online y un algoritmo de aprendizaje basado en modelos dependiendo de la forma en la que hace las predicciones. 

#### 1). En función de la manera en la que aprenden los algoritmos.. 
[[#Sección 5 - ¿Qué es el Machine Learning?]]
[[#Sección 5 - Clasificación de los sistemas de Machine Learning]]

>**Aprendizaje Supervisado y No Supervisado**
##### **Aprendizaje Supervisado** #aprendizajeSupervisado 

>**Tenemos un conjunto de datos de entrenamiento que vamos a proporcionarle a un algoritmo de aprendizaje** que lo que hace es que **ajusta una serie de parámetros internos y forma una función** que se llama en definitiva un **MODELO**, y luego nosotros **usamos ese modelo para proporcionarle nuevos datos y que nos realice predicciones.** 

Lo que **diferencia** estos algoritmos basados en #aprendizajeSupervisado **aprendizaje Supervisado** de aquellos basados en #aprendizajeNoSupervisado **aprendizaje No supervisado** es que para poder mapear la entrada a la salida, o sea **para poder construir el modelo necesita pares de entrada/salida de ejemplo**, es decir **necesita un conjunto de datos de entrenamiento que nosotros vamos a denominar como un conjunto de datos etiquetado**. 

>Un conjunto de datos etiquetados:
**Quiere decir que dentro de mi experiencia pasada, por ej estamos tratando de resolver ese problema de la detección de spam... vamos a necesitar un conjunto de correos legítimos y un conjunto de correos de spam**. 

En este **conjunto de datos que hemos recopilado** de experiencia pasada vamos a tener que **etiquetar cuáles de los correos electrónicos son legítimos y cuáles son spam**. 

Todos estos datos etiquetados le hemos proporcionado al algoritmo de aprendizaje para que construya ese modelo. 

>Este **modelo** tb se denomina **función/hipótesis**. 

>Entonces lo que caracteriza a los **algoritmos de aprendizaje supervisados** es que van a **recibir un conjunto de datos etiquetados**, es decir un analista va a tener que decir de esos datos exactamente cuáles corresponden a una u otra categoría, y el **algoritmo matemático** construirá un **MODELO** que será capaz de realizar predicciones.  

Es decir, en el futuro nosotros recibiremos únicamente la X (que sería el dato) y la Y que sería la etiqueta, entonces ya cuando hayamos construido ese modelo (función/hipótesis) lo que le proporcionaremos será un correo electrónico nuevo y ese modelo será capaz de predecir esa Y de manera automática y por supuesto sin que ese correo electrónico nuevo X que le proporcionamos pertenezca al conjunto de datos original con el que se formó el modelo. 

| X (email-datos de entrada) | **Y (g) (etiqueta)** |
| -------------------------- | -------------------- |
| Email 1                    | SPAM                 |
| Email 2                    | NO SPAM              |
| Email 3                    | SPAM                 |

>Concretamente existen **2 técnicas** de **Aprendizaje Supervisado** #aprendizajeSupervisado que son las técnicas basadas en: 

**1. Regresión** #regresión

**2. Clasificación**. #clasificación

>Ambas se diferencian en el **valor que intentan predecir**, en este caso en el tipo de valor **que es la Y**. 

###### 1. **Aprendizaje Supervisado**. REGRESIÓN: 
  
Este algoritmo se caracteriza porque **intenta predecir valores continuos**, este quiere decir que son **valores que se van a encontrar dentro de un rango muy amplio de valores**. 

>Por ej un problema que resolveríamos con técnicas de #machine_learning basadas en #aprendizajeSupervisado y en #regresión sería un problema en el que tratemos de predecir el coste que tendría una casa o un incidente de seguridad en base a una serie de características de entrada, ya que el costo que puede tener una casa está dentro de un rango muy amplio de valores, por lo que se corresponde con un valor continuo. 

Por ejemplo, tratamos de **predecir el costo que tendría un incidente de seguridad**, entonces lo primero que tengo que hacer es recopilar información sobre accidentes que han ocurrido en el pasado (recopilar esa experiencia, información). 

Al recopilar esa información, un algoritmo no va a entender lo que es un incidente, tengo que extraer una serie de características de ese incidente que le pueda proporcionar al algoritmo asociadas también con la etiqueta, es decir con el valor de salida que en este caso será el costo que tuvo el incidente en el pasado. 

Imaginemos que extraigo una característica significativa de ese incidente como puede ser: 

-  El número de equipos que se vieron afectados: entonces voy a fijarme y extraigo el dato del número de equipos que se vieron afectados (esto sería nuestra X) 

- Otra de las cosas que tengo que extraer es el costo que tuvo ese incidente, esto sería lo que quiero que mi algoritmo realice como predicción (sería nuestra variable Y, la predicción) 

| X (n equipos afectados) | Y (predicción - costo indicente) |
| ----------------------- | -------------------------------- |
| 40                      | 1000                             |
| 120                     | 12000                            |

Si representamos gráficamente nuestras variables, 
**X:** número de equipos afectados, 
**Y:** costo del incidente, 

Entonces tendremos una gráfica de puntos donde tendremos el número de los incidentes registrados y el costo de esos incidentes. 

Donde en un punto (incidente en concreto) se tuvo un número determinado de equipos afectados, por ejemplos unos 40 equipos afectados y tuvo un costo de 1000 dólares. 

Los algoritmos basados en #aprendizajeSupervisado y en #regresión lo que hacen es recoger estos **datos que están etiquetados** y van a construir una **función/hipótesis, es decir un modelo,** entonces la función matemática que van a crear es algo similar a una **recta** (esta sería nuestra función/hipótesis o modelo). 

>Esto quiere decir que después de haber analizado nuestro conjunto de datos de experiencia pasada y después de utilizar una serie de algoritmos y actualizar ajustar los parámetros internos del algoritmo, **este ha llegado a una función que se adapta de la mejor manera a la tendencia de nuestro conjunto de datos** de experiencia pasada. 

>Una vez que se ha **adaptado a la tendencia de nuestros datos**, nosotros podemos usar esa función matemática para realizar predicciones. 

Por ejemplo, si nuestra empresa sufre un incidente de seguridad en el que se ven afectados son 2000 equipos, al utilizar esta función/hipótesis nos dice que en base a la información que le hemos proporcionado, nos dice que el costo de ese incidente será tanto. 
>Entonces así nuestro **modelo** está haciendo **predicciones en base al valor de X**, le **pasamos valores de X** y este **modelo me devuelve la variable Y** que sería la **predicción**... 
>Y esta **función el modelo** la construyó en base al **conjunto de datos etiquetados** porque es un **ALGORITMO BASADO EN APRENDIZAJE SUPERVISADO**. #aprendizajeSupervisado  

Estos algoritmos se utilizan particularmente para tareas de regresión. 

###### 1. **Aprendizaje Supervisado**. CLASIFICACIÓN:

Tenemos otro tipo de tareas también para resolver que son las que se basan en clasificación.  

>Por ejemplo, la tarea de clasificar si un correo es legítimo o SPAM. 

En este caso los algoritmos basados en #aprendizajeSupervisado más concretamente en #clasificación se caracterizan porque intentan predecir un **valor discreto**. 

>En este caso, a diferencia del valor continuo, este se va a encontrar dentro de un **rango muy acotado** xq el valor que tiene que predecir por ej en el caso del correo electrónico estará entre un rango muy acotado porque son sólo 2 valores (SPAM, NO SPAM). 

De nuevo un algoritmo de #machine_learning no entiende un correo electrónico como tal por lo que no puedo extraer así el correo electrónico sino una serie de características y asociarlas con su etiqueta. 

>Imaginemos que de cada uno de los correos electrónicos que tengo en mi conjunto de datos (de esos correos pasados que etiqueté como spam y no spam) extraigo una característica como por ejemplo el número de tags html que hay en el correo porque cuantos más haya es más probable que sea un correo spam. 

**X:** número de tags html (característica que extraigo de cada correo) 

**Y:** el tipo de correo (si es SPAM o no)  - Etiquetamos SPAM = 1, NO SPAM = 0 

El algoritmo de ML tiene que traducir este texto de spam o no a un valor numérico, entonces consideramos que un correo spam será el valor 1 y no spam el valor 0. 

>Entonces tendremos valores (puntos) en la gráfica para Y = 0 y para Y = 1 a lo largo del eje x. Esto nos muestra en la gráfica que a medida que aumenta el número de tags html las probabilidades que sea un spam son más altas.  

>Acá el algoritmo nos va a construir una **función/hipótesis** que nos mostrará que todo lo que se encuentre a la derecha de la función lo considerará un SPAM y todo lo que se encuentre a la izquierda de la función lo considerará No SPAM. 

>Esta función la construye **visualizando nuestra tendencia de datos** eligiendo un número a partir del cual los clasifica como spam o no spam. 

Cuando yo ponga un correo electrónico nuevo, recogemos el número de tags y si se encuentra a la derecha... El algoritmo va a determinar que ese correo será un spam. 

>Se lo suele hacer con **muchas características (X)**, además del número de tags por ejemplo:

**X1:** número de tags html 

**X2:** número de palabras en otros idiomas. 

**Y:** característica que determina si ese correo es spam o no spam. 

Como tengo un gráfico de 2 entradas (x1 y x2) no puedo representar Y entonces vamos a hacerlo de modo visual, SPAM (1) será representado como un círculo y NO SPAM (0) será representado como una X. 

La representación gráfica estará dada por círculos y cruces entonces nos indica que un punto por eje dado por una cruz tiene un número determinado de tags (x1) y un número determinado de palabras en otro idioma, entonces en base a eso el algoritmo lo clasifica como No spam. 

>**Conclusión:** el algoritmo de #machine_learning lo que hace es recoger estos datos y construir una función/hipótesis o modelo que se adapte a esta tendencia y que permita realizar predicciones. 

Llega un nuevo correo y se sitúa en algún punto de la gráfica con tantas palabras en otro idioma y un número determinado de tags HTML, por lo que se va a situar en algún punto de la gráfica y nuestra función/hip o modelo va a determinar si es spam o no en base a dónde se sitúe (en base a sus características de entrada X)

##### **Aprendizaje NO Supervisado** #aprendizajeNoSupervisado 

**3 diferencias claves con el #aprendizajeSupervisado:**

>1. Estas técnicas van a **inferir una función**, en el #aprendizajeSupervisado lo que se hacía era crear o construirse una función o modelo en base al ajuste de una serie de parámetros internos. 

>2. Su **objetivo** es **describir la estructura de un conjunto de datos**, es decir que aquí no está hablando de que su objetivo sea predecir como en el #aprendizajeSupervisado, aquí el objetivo es **describir los datos que le estamos proporcionando**. 

>3. Por otro lado, habla de que el **conjunto de datos que va a recibir será un conjunto de datos sin etiquetar** (es decir que no se han clasificado ni categorizado previamente). 

Estos algoritmos **también van a recibir un conjunto de datos que estarán sin etiquetar** (es decir nosotros no vamos a decirle para cada ejemplo de dato a qué categoría pertenece), simplemente le proporcionamos los datos a un algoritmo de #machine_learning y este algoritmo va a **inferir una función** que también será una **función/hipótesis** y el 

>**objetivo principal de esta función** no va a estar tan relacionado con la predicción, sino que estará más **relacionado con describir la estructura de este conjunto de datos sin etiquetar** que le estamos pasando 

Cjto de datos sin etiquetar -> algoritmo de ML -> inferir una función/hip -> describir la estructura de este conjunto de datos sin etiquetar 

>Entonces en un gráfico veremos representado, por ejemplo en función de los datos que le pasemos, veremos una determinada tendencia de esos datos, **entonces va a describir una estructura en base a la similitud de los ejemplos de nuestro conjunto de datos**, en base a la distancia y una serie de características, **nos va a proporcionar por ejemplo 2 agrupaciones que nos van a decir que el conjunto de datos se divide en 2 grupos principales** de ejemplos en las que en un grupo están **ejemplos que están relacionados entre ellos** y en el otro grupo otros ejemplos que también se relacionan entre ellos. 

En este caso, **a diferencia del #aprendizajeSupervisado** de clasificación donde teníamos el conjunto de datos etiquetados... X1, X2 e Y, **en este caso eliminaríamos los datos de Y (la predicción), o sea no tenemos la etiqueta de los datos**, 

>Acá lo único que tenemos son las **características de entrada**. 

###### **¿Cómo funcionan entonces estos algoritmos?** 

Imaginemos que representamos el conjunto de datos dados por X1 y X2 como en el caso de correos spam y no spam, entonces empezamos a representarlos y tendremos puntos en el gráfico que van a representar uno y otro correo electrónico, los representamos a los puntos todos de la misma forma (ya no como una cruz o un círculo) porque no tenemos la etiqueta entonces no sé cuál de ellos son spam y cuáles no, lo único que tenemos son las características de entrada. 

>Entonces esperamos que **este algoritmo recoja los datos y genere una función/hipótesis** (por ejemplo, marcando en círculo cada grupo de puntos), esto quiere decir que en base a una serie de **métricas internas que tiene este algoritmo como por ejemplo la similitud entre los datos, la distancia, entre otras,** ha determinado que la estructura de los datos es la que nos mostrará en el gráfico que en este caso **nos muestra que hay 2 grupos grandes de subconjuntos de datos** dentro de nuestro conjunto de datos original. 

El objetivo de esto es que después un analista recoja esto que nos ha proporcionado el algoritmo y lo analiza de manera que así esa persona luego de ver la estructura de distribución y agrupación de esos datos... llegue a la conclusión de que en uno de los subconjuntos que nos ha extraído el algoritmo tenemos todos los correos spam, mientras que en el otro subconjunto que nos ha extraído el algoritmo tenemos casi todos los correos no spam. 

>Este tipo de algoritmos sirven entonces para **tratar grandes volúmenes de información que son imposibles de etiquetar** de manera manual en una lista porque son muchísimos registros, entonces recoge todos los datos y ese algoritmo **nos proporciona esa estructura de disposición de los datos y analizándola**, nosotros podamos ser capaces de obtener intuiciones de nuestro conjunto de datos que nos permita avanzar o crear reglas o aplicar otras técnicas o hacer lo que queramos. 


#### 2). En función en la manera en la que aprenden en el tiempo: APRENDIZAJE ONLINE Y BATCH 
[[#Sección 5 - Clasificación de los sistemas de Machine Learning]]

La anterior clasificación de los algoritmos era en base a la manera en la que aprendía, o sea la manera en la que el algoritmo construye esa función/hipótesis o modelo. 

>Acá vamos a centrarnos en la manera en la que el algoritmo ingiere ese conjunto de datos para construir el modelo, es decir cómo aprende y obtiene los datos a lo largo del tiempo. 

##### **Aprendizaje Batch** 

>Se caracteriza porque **no aprenden de manera incremental**, o sea que se entrenan utilizando todos los datos disponibles en un momento determinado del tiempo. 

Por ejemplo, cuando hablábamos de utilizar ML en la detección de correos electrónicos spam teníamos que el analista analizaba el problema, luego seleccionaba un algoritmo de ML, seleccionaba un conjunto de datos que fuese significativo del problema que quería resolver y le proporcionaba ese conjunto de datos al algoritmo en lo que llamábamos entrenamiento del algoritmo para que construyera el modelo, o sea para que formara la función/hipótesis de la tendencia de ese conjunto de datos. 

>Si nosotros realizamos este proceso de entrenamiento, **este proceso de ajustar la función/hipótesis a la tendencia del conjunto de datos en un momento determinado en el tiempo**, es decir, recojo todos mis datos disponibles, se los proporciono al algoritmo de ML y ajusto esta función/hipótesis, este algoritmo está utilizando una **técnica basada en #aprendizaje_batch**. 

En el momento en el que he terminado de entrenar al algoritmo por completo (de ajustar esa función/hipótesis por completo a la tendencia de nuestros datos) es cuando pasamos a la sgte fase de evaluación en la que verificamos que ese modelo se comporta correctamente para ejemplos que no estaban en ese conjunto de datos inicial que usamos para entrenar. 

Como ya vimos, en el caso que fuese correcto lo ponemos en producción, en el caso que no fuera correcto pasaría a la fase de análisis de errores. 

>Esto es lo que caracteriza a las técnicas de #machine_learning que se basan en #aprendizaje_batch, donde vamos a **utilizar todo nuestro conjunto de datos en un momento determinado del tiempo para entrenar nuestro algoritmo**, obtener una función/hipótesis o modelo ajustado y ya después utilizar ese modelo para realizar predicciones. 

>En el caso de que estuviéramos utilizando un algoritmo de #machine_learning basado en #aprendizajeNoSupervisado (si también se basa en #aprendizaje_batch) es **proporcionarle todo nuestro conjunto de datos para que saque una estructura para que saque una serie de intuiciones de todos los datos que tenemos disponibles en ese momento**. 

##### **Características de un algoritmo basado en aprendizaje batch** 

>Como los sistemas basados en este tipo de aprendizaje **no aprenden de manera incremental, o sea se entrenan usando los datos disponibles en un determinado momento en el tiempo**...  

1) Si se desea que el sistema **se adapte a un nuevo tipo de dato, se debe entrenar de nuevo con todos los datos disponibles**. Si nosotros estamos entrenando en un momento determinado del tiempo, nuestro modelo con todos los datos que tenemos en ese momento disponibles, si en algún momento esos datos cambian por ejemplo en el caso de los correos de spam, si los atacantes cambian el tipo de correo de spam para evitar ser detectados, y aumentamos nuestro conjunto de datos con nuevos correos electrónicos de spam, tendríamos que volver a reentrenar nuestro algoritmo con el nuevo conjunto de datos del que disponemos. 

>Por lo que este tipo de algoritmo **deben reentrenarse normalmente de nuevo con todos los datos cuando el conjunto de datos cambia**. 

2) Otra característica es que es una solución sencilla, es mucho más sencilla de la de aprendizaje online porque únicamente debemos tener nuestros datos y entrenar ese algoritmo en un momento determinado. 

3) **Funciona bien para sistemas que no requieran de un conjunto de datos muy grande ni que tengan que adaptarse a nuevos datos de manera muy rápida** ya que como vimos arriba, si los datos cambian tenemos que reentrenar el algoritmo, por ende, si los datos no cambian con mucha frecuencia, este tipo de técnicas suele ser la ideal. 

4) Por otro lado, siguiendo lo anterior, **este tipo de aprendizaje está más restringido para dispositivos con una capacidad limitada de recursos** (ya que funciona bien cuando los sistemas **no requieren un conjunto de datos muy grande**), como por ejemplo un **smartphone, una tablet o cualquier dispositivo de este estilo**. 

>Esto es porque esa **fase de construcción del modelo**, de **ajustar esa función/hipótesis es la fase que más recursos computacionales va a consumir**, entonces **cuantos más datos tengamos más recursos computacionales vamos a requerir** para poder procesar todos esos datos. 

Entonces si nuestro problema se puede resolver con un conjunto de datos pequeño, este enfoque será el correcto ya que no requeriremos muchos recursos computacionales. 

Si para resolver nuestro problema necesitamos un conjunto muy grande de datos, para poder procesar este volumen de información, requerirá mucha memoria, disco, etc 

##### **Aprendizaje Online**  #aprendizaje_online

>Estos se caracterizan porque se entrenan incrementalmente mediante el consumo incremental de datos, ya sea individuales o en pequeños grupos. 

>Es decir, **ya no voy a entrenar al algoritmo con todos los datos disponibles en un momento determinado en el tiempo, sino que poco a poco voy a ir entrenándolo con cada uno de los ejemplos de mi conjunto de datos** (datos individuales) o con cada subconjunto de datos (grupos pequeños de datos o **mini-batches**). 

**ESQUEMA** 

Tenemos como en el caso anterior, el analista que hará el análisis del problema y seleccionará un conjunto de datos inicial (miles y millones de registros). Recogerá un subconjunto de datos y hará un entrenamiento inicial de nuestro algoritmo, es decir, ajustará un poco los parámetros de nuestro modelo, o sea la función/hipótesis a la tendencia de nuestro conjunto de datos, luego lo pondrá en evaluación y verá si esto es correcto o no. 

Si ve que los resultados que proporciona con ese ajuste que hizo más o menos son correctos, lo pone en producción. 

Luego a lo largo del tiempo va a ir recogiendo otro subconjunto de datos y a la vez que realiza predicciones, va a ir entrenando el modelo, o sea irá poco a poco mejorando en el tiempo pasándole **subconjuntos de datos o pequeños grupos de datos denominados mini-batches**. 

###### **Características de un algoritmo basado en aprendizaje online** 

Como son **sistemas de aprendizaje que se basan en un entrenamiento incrementalmente.**.. 

1) Son **soluciones ideales para sistemas que reciben datos continuamente y requieren adaptarse a ellos de manera rápida**. Se diferencian de los algoritmos con mecanismo de aprendizaje de tipo batch porque estos no se pueden adaptar bien a nuevos datos porque tienen que entrenarse nuevamente para estos nuevos datos. 

> En este caso si podemos, tenemos un conjunto de datos inicial, entreno el algoritmo con este conjunto de datos iniciales y después lo pongo en producción y, **a medida que va pasando el tiempo y voy recibiendo nuevos datos**, puedo **reentrenar o mejorar un poco mi modelo, entonces vamos recibiendo esos nuevos datos en tiempo real** y le **vamos proporcionando al modelo que está prediciendo de manera que vaya mejorando de a poco**. 

2) Entonces este tipo de aprendizaje es muy **útil para esos sistemas que continuamente están recibiendo datos**. 

3) Es capaz de **lidiar con grandes conjuntos de datos que puede que no entren en una sola máquina, ya no necesito entrenar el algoritmo con todo el conjunto de datos de golpe** en un momento dado, sino que puedo partir de mi conjunto de datos e ir entrenando de a poco. 

> Si nuestro problema requiere un conjunto de datos muy grande, la posible solución es utilizar un #aprendizaje_online  

4) También este tipo de aprendizaje tiene algunas **limitaciones** como, por ejemplo, pueden ser muy inestables si se consumen **datos de baja calidad**. 

>**Ejemplo:** 
>Tenemos un sistema que va mejorando poco a poco con datos que va recibiendo en tiempo real, si estos en algún momento comienzan a ser datos de baja calidad, que no sean representativos del problema, van a afectar el modelo y **degradar la capacidad de predicción que tiene nuestro modelo en ese momento**. 

>Es importante **filtrar bien los datos antes de proporcionarlos al algoritmo** porque sino pueden degradar el algoritmo.

>Hay que tener cuidado con los datos que se van proporcionando en tiempo real porque si se lo hace sin un filtrado previo puede provocar una falla en nuestro modelo. 

5) Es importante que se **incorporen una serie de módulos que se encarguen de pre-filtrar** esos datos y asegurarse que esa sea una **información de calidad** (datos correctamente normalizados, datos de calidad, etc) 

>Esto hace que estos sistemas sean más complejos que los sistemas basados en aprendizaje batch. 

##### **3). En base a la manera en que realizan las predicciones: APRENDIZAJE BASADO EN INSTANCIAS Y EN MODELOS** 
[[#Sección 5 - Clasificación de los sistemas de Machine Learning]]

Ya clasificamos a los algoritmos de #machine_learning en base a la **manera en la que aprendían** #aprendizajeSupervisado y #aprendizajeNoSupervisado . La **manera en la que se entrenaban o recibían esos datos a lo largo del tiempo**. #aprendizaje_batch y #aprendizaje_online  

>Ahora vamos a clasificar a estos algoritmos en **base a la manera en la que realizan las predicciones** o nos proporcionan **esa estructura de la que hablábamos en las técnicas de #aprendizajeNoSupervisado **. 

**Tenemos 2 subcategorías que son:** 

1) Aprendizaje basado en Instancias 

2) Aprendizaje basado en Modelos 

En todo momento hasta ahora hablamos sobre **Modelos, donde dijimos que los algoritmos de ML creaban modelos (función/hipótesis) con el que realizaban predicciones o nos proporcionaban una estructura**, pero en ningún momento hablamos de instancias.  También existen un tipo de algoritmo de ML que se basan en este concepto. 

>**MODELO:**
   Nos realizan predicciones en base a datos etiquetados #aprendizajeSupervisado 
   Nos proporciona una estructura en la cual están distribuidos los datos #aprendizajeNoSupervisado 

##### **Aprendizaje basado en Instancias** 

>En estos casos, el **sistema aprende los ejemplos del conjunto de datos de entrenamiento** y luego intenta generalizar para nuevos ejemplares. 

>Acá se requiere una **medida de similitud** 

**Ejemplo:** 
Usando el ejemplo de la detección de correos spam, vamos a representar en un gráfico nuestro conjunto de datos etiquetados (vamos a suponer que estamos utilizando técnicas basadas en #aprendizajeSupervisado  y además basado en #aprendizaje_en_instancias). 

Entonces, si extraigo 2 características de mi conjunto de datos como por ej el número de tags (X1) y el número de palabras en otro idioma (X2). 

Representamos en 
morado: correos etiquetados como spam, y 
en verde: correos etiquetados como no spam. 

Tengo este conjunto de datos y si estoy usando una técnica de aprendizaje basado en instancias, este **algoritmo lo que hará será recoger nuestro conjunto de datos de entrenamiento (que es un conjunto de datos etiquetados) y va a aprender exactamente las características que tienen cada uno de los correos electrónicos que forman parte de nuestro conjunto de datos**. 

Entonces va a aprender que un punto del gráfico (un determinado correo) va a tener un determinado número de tags y tiene un número concreto de palabras en otro idioma y que está clasificado como Spam, así va a ir aprendiendo cuáles son las características concretas de cada uno de los ejemplos o instancias de nuestro conjunto de datos. 

De esta manera, **cuando nosotros recibimos un nuevo correo electrónico, es decir cuando el algoritmo ya terminó de aprender exactamente como son todos los ejemplos de nuestro conjunto de datos y lo ponemos en producción**,
Si recibimos un nuevo email que extraemos esas 2 características (número de tags y número de palabras en otro idioma)... imaginemos que ese nuevo correo cae en una posición determinada en el gráfico, lo que haría nuestro algoritmo sería ir a lo que ha aprendido de nuestro conjunto de datos y diría que ese correo nuevo que tiene esas características de entrada (X1 y X2) coincide exactamente con otro de los que yo tenía en mi conjunto de datos y que estaba clasificado como Spam, por lo tanto ese nuevo correo que le estamos proporcionando es Spam, y ese sería el resultado o predicción de nuestro algoritmo. 

**¿Qué pasa si el nuevo correo electrónico no coincide con ninguna de las instancias o ejemplos de nuestro conjunto de datos?** 

>Para esto existe la **medida de similitud**. 
  **Por ejemplo:**
  Nuestro nuevo correo electrónico cayera en alguna parte del gráfico que no coincida con ningún otro punto (ejemplar o instancia del conjunto de datos), cuando extraemos el número de tag html y tendrá un número concreto de palabras en otro idioma, **entonces este algoritmo lo que hará será utilizar la medida de similitud para comparar con los ejemplos/instancias del conjunto de datos de entrenamiento que ha aprendido y procesará que ese ejemplo nuevo que está tratando de predecir si es spam o no y va a calcular la  similitud que tiene con los ejemplos/instancias del conjunto de datos**, observará que está más cerca de algún otro punto de la gráfica por ejemplo, o sea se fijará qué ejemplos tiene cerca ese punto nuevo  y cuáles están más alejados. 

Entonces c**omo es más similar a todos los puntos/ejemplos/instancias de nuestro conjunto de datos que están clasificados**, en este caso, como correos electrónicos de spam, el algoritmo va a predecir para este nuevo correo electrónico del que ha extraído esas características de entrada (x1 y x2) que se trata de un correo electrónico spam porque se encuentra más cerca y es más similar al resto de los datos que son correos de spam. 

>En esto consisten las técnicas basadas en instancias, fundamentalmente se centran en las instancias o ejemplos de nuestro conjunto de datos de entrenamiento y mediante una serie de **medidas de similitud** realiza las predicciones. 

##### **Aprendizaje basado en Modelos** 

>Sería todo lo que fuimos viendo a lo largo de las secciones anteriores. 

Si tenemos un conjunto de datos, nuestros correos legítimos en una zona del gráfico y los correos de spam por otra zona del gráfico, en ese caso el algoritmo:

>en todo ese proceso de **aprendizaje/entrenamiento no se fijará concretamente en cuáles son las características de los ejemplos de nuestro conjunto de datos para después comparar con las características de un nuevo ejemplo que nos llegue, sino que lo que hace es construir una función/hipótesis o modelo que se adapte lo mejor posible a la tendencia de nuestros datos**. 

>Es decir, **construirá un modelo o función/hipótesis**, de manera que cuando llegue un nuevo ejemplo que tenga un determinado número de tags (X1) y un determinado número de palabras en otro idioma (X2), lo podamos evaluar con esa función y como cae por ejemplo a la derecha de la función o del gráfico (en el grupo donde están los correos spam), esa función nos devolverá un resultado que en este caso sería que ese nuevo ejemplo se trata de un correo spam. 

####### **Acá NO se fijará en la distancia o en la similitud que hay entre ese nuevo ejemplo y los ejemplos que tiene cercanos o alejados dentro del conjunto de datos de entrenamiento como el #aprendizaje_en_instancias .** 

>Acá la evaluación/predicción se **realiza a partir de esa función/hipótesis o modelo**. 

>Para que esto pueda funcionar lo que se requiere en un algoritmo que utiliza un mecanismo de aprendizaje basado en modelos es una serie de parámetros del modelo.  


>**Conclusión:** 
>Se diferencian principalmente en la **forma en la que realizan las predicciones** y lo que utilizan para realizar estas predicciones, **ya sea una medida de similitud** (en el caso del #aprendizaje_en_instancias ) o una **función matemática** #aprendizaje_en_modelos que tiene una serie de parámetros que se fueron ajustando durante ese proceso de aprendizaje (**aprendizaje basado en modelos**).


