### Bioinformatics for beginners
### 2. How to manipulate gene expression data from NCBI GEO in R using dplyr

**References:**
- https://www.youtube.com/watch?v=4CkRXGWmAbU&list=PLJefJsd1yfhbIhblS-85alaFsPdU00DaA&index=2
- https://www.bioconductor.org/packages/devel/bioc/vignettes/GEOquery/inst/doc/GEOquery.html
- https://statisticsglobe.com/r-dplyr-join-inner-left-right-full-semi-anti

- **Index:** [[4 - Indexes/RNA sequencing|RNA sequencing]]

**Tags:** [[3 - Tags/RNA Sequencing|RNA Sequencing]]

----
   NCBI > GEO > GSE183947 (Pongo en el buscador con GEO DataSet en NIH)

Series GSE183947		Query DataSets for GSE183947
Status:	Public on Sep 15, 2021
Title:	Identification of five cytotoxicity-related genes involved in the progression of breast cancer.

Organism: Homo sapiens

Experiment type:  Expression profiling by high throughput sequencing
Summary: Breast cancer is one of the deadly tumors in women, and its incidence continues to increase. This study aimed to identify novel therapeutic molecules using RNA sequencing (RNAseq) data of breast cancer from our hospitals.
 	
Overall design	30 pairs of normal and cancerous tissues from the same excision were collected from the Affiliated Cancer Hospital of Guangzhou Medical University, the Affiliated Cancer Hospital of Sun Yat-sen University and Guangzhou Army General Hospital. RNA sequencing was performed by Guangzhou Huayin Health medical Group. Original reads of RNA sequencing data were normalized as FPKM data.

Platforms (1)	
GPL11154	Illumina HiSeq 2000 (Homo sapiens)
Samples (60)
More... More...
GSM5574685	tumor rep1 
GSM5574686	tumor rep2
GSM5574687	tumor rep3


Supplementary file	Size	Download	File type/resource
GSE183947_fpkm.csv.gz	2.3 Mb	(ftp)(http)	CSV

Tengo que seleccionar en http para descargar la bdd de GSE183947 en formato csv.
Si viene como .gz tengo que descompirmirlo, en la terminal con el comando gunzip y luego el nombre del archivo.

	     -------------------------------------------------------------------------


1. Reading in expression matrix (FPKM) into R
2. Fetching metadata/clinical data using GEOquery R pacakge
3. Demostrate useful functions to manipulate the data:
   tidy data: select(), filter(). 
   reshaped data: gather()
   Join data: left_join()
   explore data: mutate(), group_by(), summarize(), arrange()

(Para ver dónde estoy ubicada)
> getwd()
[1] "C:/Users/Emiliana/OneDrive/Documentos"



script to manipulate gene expression data (GSE183947)
setwd("C:/Bioinformática/RNA Sequencing")

 load libraries
library(dplyr)
library(tidyverse)
library(GEOquery)

# ----- READ IN THE DATA ---------
file.choose()
data <- read.csv(file = "C:\\Bioinformática\\RNA Sequencing\\GSE_GEO_DataSet\\GSE183947_fpkm.csv\\GSE183947_fpkm.csv")
dim(data)
str(data)
summary(data)
head(data)


> dim(data)
[1] 20246    61
> str(data) 
'data.frame':	20246 obs. of  61 variables:

> head(data)
         X CA.102548 CA.104338 CA.105094 CA.109745 CA.1906415 CA.1912627
1   TSPAN6      0.93      1.97      0.00      5.45       4.52       4.75
2     TNMD      0.00      0.00      0.00      0.00       0.00       0.00
3     DPM1      0.00      0.43      0.00      3.43       8.45       8.53
4    SCYL3      5.78      5.17      8.76      4.58       7.20       6.03
5 C1orf112      2.83      6.26      3.37      6.24       5.16      13.69
6      FGR      4.80      1.83      0.00      4.23      15.87       8.56

#Matrix 
Rows: Genes
Columns: Samples

En esta Matriz no tengo información sobre cuál muestra corresponde a la sample normal o a la tumor sample.
Esta información la obtengo del metadata file. La puedo descargar del NCBI pero lo que se suele hacer es obtenerla a partir del GEO QUERY package

Estos meta datos requieren de múltiples pasos de manipulación de datos

The counts are the number of reads mapping to that gene in that sample.
Counts measure gene expression.

                SRR1039508 
ENSG00000000003        679

679 sería el conteo de las lecturas (reads) que mide la expresión de ese gen ENSG00000000003 en la muestra SRR1039508.



------. OBTENER LOS META DATOS .--------
Puedo obtener estos metadatos a partir del GEO QUERY package.
usando el comando getGEO() que recibe como primer parámetro el número de id del código de acceso GEO del ARN-seq, y como 2do parámetro poner como TRUE el GSEMatrix porque quiero que me devuelva una matriz.

# get metadata -------- library(GEOquery)
gse <- getGEO(GEO = 'GSE183947', GSEMatrix = TRUE)

> gse <- getGEO(GEO = 'GSE183947', GSEMatrix = TRUE)
Found 1 file(s)
GSE183947_series_matrix.txt.gz

> gse
$GSE183947_series_matrix.txt.gz
ExpressionSet (storageMode: lockedEnvironment)
assayData: 0 features, 60 samples 
  element names: exprs 
protocolData: none
phenoData
  sampleNames: GSM5574685 GSM5574686 ... GSM5574744 (60 total)
  varLabels: title geo_accession ... tissue:ch1 (41 total)
  varMetadata: labelDescription



-----.EXTRAER LA INFORMACIÓN FENOTÍPICA ASOCIADA CON LAS MUESTRAS DEL OBJETO gse[[1]] .------
metadata <- pData(phenoData(gse[[1]]))
head(metadata)

> dim(metadata)
[1] 60 41

gse --> es una lista (posiblemente un objeto de tipo ExpressionSet o una lista d eobjetos relacionados con datos genómicos).

gse[[1]] --> está accediendo al primer elemento de esta lista que se corresponde con un objeto que contiene los datos de un experimento específico (datos de expresión génica)

pData(phenoData(gse[[1]]) --> La función phenoData() extrae la información fenotípica asociada con las muestras del objeto gse[[1]]. Estos datos son las características de las muestras, como el tipo de tto, edad, tiempo, o cualquier otra variable experimental que describe las condiciones de las muestras.

pData() --> es una función que extrae los datos fenotípicos en forma de data frame del objeto de los datos fenotípicos que obtuvimos con phenoData(). O sea que extrae los valores fenotípicos asociados con las muestras del experimento, en un formato de tabla que pueda ser analizado, filtrado o manipulado.


>head(metadata)
           data_row_count    instrument_model library_selection library_source
GSM5574685              0 Illumina HiSeq 2000              cDNA transcriptomic
GSM5574686              0 Illumina HiSeq 2000              cDNA transcriptomic
GSM5574687              0 Illumina HiSeq 2000              cDNA transcriptomic
GSM5574688              0 Illumina HiSeq 2000              cDNA transcriptomic
GSM5574689              0 Illumina HiSeq 2000              cDNA transcriptomic
GSM5574690              0 Illumina HiSeq 2000              cDNA transcriptomic
           library_strategy
GSM5574685          RNA-Seq
GSM5574686          RNA-Seq
GSM5574687          RNA-Seq
GSM5574688          RNA-Seq
GSM5574689          RNA-Seq
GSM5574690          RNA-Seq

           supplementary_file_1 donor:ch1 metastasis:ch1   tissue:ch1
GSM5574685                 NONE    102548            yes breast tumor
GSM5574686                 NONE    104338            yes breast tumor
GSM5574687                 NONE    105094            yes breast tumor
GSM5574688                 NONE    109745             no breast tumor
GSM5574689                 NONE   1906415             no breast tumor
GSM5574690                 NONE   1912627            yes breast tumor 



------. MANIPULACIÓN DE LOS METADATOS .-----------
# select, mutate, rename ------------
metadata.modified <- metadata %>%
  select(1,10,11,17) %>%
  rename(tissue = characteristics_ch1) %>%
  rename(metastasis = characteristics_ch1.1) %>%
  mutate(tissue = gsub("tissue: ", "", tissue)) %>%
  mutate(metastasis = gsub("metastasis: ", "", metastasis))

head(metadata.modified)

                title       tissue metastasis description
GSM5574685 tumor rep1 breast tumor        yes   CA.102548
GSM5574686 tumor rep2 breast tumor        yes   CA.104338
GSM5574687 tumor rep3 breast tumor        yes   CA.105094
GSM5574688 tumor rep4 breast tumor         no   CA.109745
GSM5574689 tumor rep5 breast tumor         no  CA.1906415
GSM5574690 tumor rep6 breast tumor        yes  CA.1912627



# looking at gene expression data ---------
head(data)

       X CA.102548 CA.104338 CA.105094 CA.109745 CA.1906415 CA.1912627 CA.1924346
1   TSPAN6      0.93      1.97      0.00      5.45       4.52       4.75       3.96
2     TNMD      0.00      0.00      0.00      0.00       0.00       0.00       0.00
3     DPM1      0.00      0.43      0.00      3.43       8.45       8.53       7.80
4    SCYL3      5.78      5.17      8.76      4.58       7.20       6.03       9.05
5 C1orf112      2.83      6.26      3.37      6.24       5.16      13.69       6.69
6      FGR      4.80      1.83      0.00      4.23      15.87       8.56      13.28



# ---------- reshaping data - from wide to long--------
data.long <- dat %>%
  rename(gene = X) %>%
  gather(key = 'samples', value = 'FPKM', -gene)

En el data_frame llamado data donde tenemos los genes (filas) y las samples (columnas) vamos a renombrar la columna X por gene
Pongo key = "simples" porque quiero que mis muestras sean la key.
Values serían los valores de la columna samples, en este caso quiero llamarlos FPKM.
 
Ponemos -gene para que no tome los valores de la columna gene, así no toca la columna de genes.


> head(data.long)
      gene   samples FPKM
1   TSPAN6 CA.102548 0.93
2     TNMD CA.102548 0.00
3     DPM1 CA.102548 0.00
4    SCYL3 CA.102548 5.78
5 C1orf112 CA.102548 2.83
6      FGR CA.102548 4.80


> head(metadata.modified)
                title       tissue metastasis description
GSM5574685 tumor rep1 breast tumor        yes   CA.102548
GSM5574686 tumor rep2 breast tumor        yes   CA.104338
GSM5574687 tumor rep3 breast tumor        yes   CA.105094
GSM5574688 tumor rep4 breast tumor         no   CA.109745
GSM5574689 tumor rep5 breast tumor         no  CA.1906415
GSM5574690 tumor rep6 breast tumor        yes  CA.1912627

Vemos que coincide la description del df metadata.modified con la columna samples del df data.long
Entonces podemos hacer unn join 



# ---------- join dataframes = data.long + metadata.modified --------------
head(metadata.modified)

dat.long <- dat.long %>%
  left_join(., metadata.modified, by = c("samples" = "description")) 

el primer parámetro es un . que indica que se corresponde con el data frame data.long, mientras que el segundo que pongo es el 2do data frame que es metadata.modified

by = c("samples" = "description")
Pongo las columnas por medio de las cuales quiero que se unan, deben tener un matching values.


> data.long
          gene   samples   FPKM      title       tissue metastasis
1       TSPAN6 CA.102548   0.93 tumor rep1 breast tumor        yes
2         TNMD CA.102548   0.00 tumor rep1 breast tumor        yes
3         DPM1 CA.102548   0.00 tumor rep1 breast tumor        yes
4        SCYL3 CA.102548   5.78 tumor rep1 breast tumor        yes
5     C1orf112 CA.102548   2.83 tumor rep1 breast tumor        yes
6          FGR CA.102548   4.80 tumor rep1 breast tumor        yes
7          CFH CA.102548   1.37 tumor rep1 breast tumor        yes
8        FUCA2 CA.102548  21.92 tumor rep1 breast tumor        yes




# explore data ------
Para este caso quiero extraer la expresión para 2 genes(BCRA1 y 2) y compararlo con la expresión de genes de la muestra normal

# filter, group_by, summarize and arrange 
dat.long %>%
  filter(gene == 'BRCA1' | gene == 'BRCA2') %>%
  group_by(gene, tissue) %>%
  summarize(mean_FPKM = mean(FPKM),
            median_FPKM = median(FPKM)) %>%
  arrange(-mean_FPKM)


# Groups:   gene [2]
  gene  tissue               mean_FPKM median_FPKM
  <chr> <chr>                    <dbl>       <dbl>
1 BRCA1 breast tumor             10.0         6.96
2 BRCA1 normal breast tissue      7.70        6.45
3 BRCA2 normal breast tissue      3.05        1.25
4 BRCA2 breast tumor              2.04        1.6 



Este código en R utiliza la tubería (`%>%`) de `dplyr` para filtrar, agrupar, resumir y ordenar datos en un conjunto llamado `dat.long`. A continuación, te explico cada paso:

1. **`dat.long %>%`**: `dat.long` es el nombre del data frame que se pasa a través de la tubería para aplicar una serie de operaciones.

2. **`filter(gene == 'BRCA1' | gene == 'BRCA2') %>%`**: Selecciona solo las filas donde la columna `gene` tiene el valor `'BRCA1'` o `'BRCA2'`. Esto filtra el conjunto de datos para que solo incluya estos dos genes.

3. **`group_by(gene, tissue) %>%`**: Agrupa los datos filtrados por las columnas `gene` y `tissue`. Esto significa que cualquier cálculo posterior se hará dentro de cada grupo de `gene` y `tissue`.

4. **`summarize(mean_FPKM = mean(FPKM), median_FPKM = median(FPKM)) %>%`**: Dentro de cada grupo (`gene` y `tissue`), calcula dos valores resumen:
   - `mean_FPKM`: el promedio de la columna `FPKM` en cada grupo.
   - `median_FPKM`: la mediana de la columna `FPKM` en cada grupo.
   
   Estos cálculos crean nuevas columnas llamadas `mean_FPKM` y `median_FPKM`.

5. **`arrange(-mean_FPKM)`**: Ordena el resultado final de manera descendente según el valor de `mean_FPKM`. Esto significa que las filas con los valores más altos de `mean_FPKM` aparecerán primero.

### Resultado Final

Al final, el código devuelve un resumen de los datos de `BRCA1` y `BRCA2`, agrupados por `tissue`, con el promedio y la mediana de `FPKM`, y ordenados de mayor a menor según el promedio de `FPKM` en cada grupo. 

¿Te gustaría un ejemplo con datos ficticios para ver el resultado?



