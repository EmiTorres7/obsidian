### Bioinformatics 101 | 
#### 1. How to download RNA-Seq data from NCBI GEO | Bioinformatics for beginners

**Reference:**
- **https://www.youtube.com/watch?v=2RFYKTvCXHs&list=PLJefJsd1yfhbIhblS-85alaFsPdU00DaA&index=2
- **Index:** [[4 - Indexes/RNA sequencing|RNA sequencing]]

**Tags:** [[3 - Tags/RNA Sequencing|RNA Sequencing]]

----
#### Measuring Gene Expression

**There 2 maners:

**1). DNA Microarray

Esta técnica está basada en la hibridación del ADN. El ARN de las muestras son retrotranscriptas a ADN complementario y este se une a etiquetas fluorescentes.
Este ADNc es capaz de unirse a sondas que no son más que cortas secuencias de ADN que se complementan con los genes.
En el siguiente paso, la placa es lavada y el ADNc que no se haya hibridizado get wash of.
Y lo que obtenemos es una placa con diferentes intensidades de fluorescencia donde podemos identificar cuáles genes son expresados en una muestra o ambas muestras, o también podemos identificar los genes expresados entre las muestras.


**2). RNA-Seq

Los ARN de las muestras son retro transcriptos a su ADNc, estos son particionados en fragmentos y pasados por un secuenciador de ADN.
El secuenciador de ADN nos devuelve todas las reads que mapean con el genoma de referencia.

	reference genoma      gene_1   gene_2   gene_3 

	Sample_2	           reads

	Sample_1		       reads


El DNA secuenciador nos da las reads que son las que mapean con los diferentes genes.
Basado en el número de reads que mapean para el gen de referencia obtenemos una tabla "gene cuantification matrix"

Counting reads and normalization

>Gene    Sample_1    Sample_2
>
 Gene_1       0           0
 Gene_2      15          14
 Gene_3       5           7

Las filas en la Matrix de genes son los genes (Gene_1, Gene_2, Gene_3, etc)
Las columnas se corresponden con las muestras Sample1, Sample2, etc.
Valores: son los números que se corresponden con las reads que mapean con el genoma.

Por ejemplo, vemos que no hay reads que mapeen con el gene_1 en las Sample1 y Sample2.
De la misma forma, hay algunas reads que mapean con el Gene_2 en las Sample1 y en la Sample2, esos números que aparecen en la tabla se corresponden con las reads que mapean con el Gene_2 del genoma de referencia

Gene Expresión Data es necesario hacer normalización o pasos de corrección. 
Hay diferentes métodos de Normalización:
-ATPM
-ARPKM
-FPKM
-TPM

Luego de aplicar esta normalización se genera la Gene Expresión Matrix o Cuantification Matix, basada en el número de reads que son mapeadas con el genoma, así se mide la expresión de ese gen.


Example
> head(data)
         X CA.102548 CA.104338 CA.105094 CA.109745 CA.1906415 CA.1912627
1   TSPAN6      0.93      1.97      0.00      5.45       4.52       4.75
2     TNMD      0.00      0.00      0.00      0.00       0.00       0.00
3     DPM1      0.00      0.43      0.00      3.43       8.45       8.53

#Matrix 
Rows: Genes_id
Columns: Samples_names
Values: Counts

The counts are the number of reads mapping to that gene of genoma in that sample.
Counts measure gene expression.
Estos datos fueron normalizados por el método FPKM

En esta Matriz NO tengo información sobre cuál muestra corresponde a la sample normal o a la tumor sample.
Esta información la obtengo del metadata file. La puedo descargar del NCBI pero lo que se suele hacer es obtenerla a partir del GEO QUERY package.



   NCBI > GEO > GSE183947 (Pongo en el buscador con GEO DataSet en NIH)

G-ENE E-XPRESSION O-MNIBUS
GEO Database es un repositorio público de datos genómicos funcionales que admite el envío de datos conforme a MIAME. Se aceptan datos basados en matrices y secuencias.
Se proporcionan herramientas para facilitar la consulta y descarga y descarga de experimentos y perfiles de expresión génica.

Nos sirve para obtener los datos de expresión génica.

Podemos buscar los datos de 2 maneras, con el accesion id o con key words.
Cada dataset en GEO tiene un único dato de acceso ID


GSE183947 --> Este ID utilizaremos
Este data set está asociado a datos de cáncer de mama

ARN sequencing data: 
Los datos de secuenciación de ARN (RNA-seq) son perfiles de expresión génica que se obtienen a partir de la secuenciación de ARN de una muestra de tejido o célula. Estos datos permiten analizar la cantidad y la secuencia de ARN, y qué genes están activados o desactivados.

Cómo se obtienen los datos de RNA-seq:
.Se aíslan las moléculas de ARN de la muestra
.Se copian las moléculas de ARN en ADN.
.Se secuencian las moléculas de ADN resultantes.



https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE183947
Al final tengo el Gene Expression Data

Supplementary file	Size	Download	File type/resource
GSE183947_fpkm.csv.gz	2.3 Mb	(ftp)(http)	CSV


GSE183947_fpkm.csv.gz: 
Gene expresión data with normalization data

Tengo que seleccionar en http para descargar la bdd de GSE183947 en formato csv.
Si viene como .gz tengo que descompirmirlo.

Para descompirmirlo voy a mi terminal, me posiciono en la ubicación del archivo y luego uso el comando gunzip y el  nombre del archivo y ahí podemos ver que nos queda en lugar de .gz, nos queda como .csv



