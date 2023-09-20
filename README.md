# Bioinformatica_y_Metagenomica_en_los_Andes-2023
## Herramientas bioinformáticas y flujos de trabajo para el procesamiento, edición y análisis de datos WMS.

**Leonardo R. Rocabado-Villegas.** Área de Bioquímica Molecular, Instituto de Investigaciones Fármaco - Bioquímicas.
### Contacto:
email: lrocabado22@gmail.com

Ante cualquier duda consulten a cualquiera de los instructores.

### Sistema operativo
Para esta sección es recomendable la particion del disco duro con una distribución de Unix.
### Secuencias
Para disponer de los archivos que seran análizados en este curso, será necesario que abran una Terminal, e instalen el programa SRA-tools:
```
https://github.com/ncbi/sra-tools
```
Y descarguen al menos 10 de los siguientes codigos de acceso SRA.

Metagenomic Shotgun Sequencing of Surface Water Samples:

Accession: SRX20755941  Accession: SRX20755940
Accession: SRX20755939  Accession: SRX20755938
Accession: SRX20755937  Accession: SRX20755936
Accession: SRX20755935  Accession: SRX20755934
Accession: SRX20755933  Accession: SRX20755932
Accession: SRX20755931  Accession: SRX20755930
Accession: SRX20755929  Accession: SRX20755928
Accession: SRX20755927  Accession: SRX20755926
Accession: SRX20755925  Accession: SRX20755924
Accession: SRX20755923  Accession: SRX20755922
Accession: SRX20755921  Accession: SRX20755920
Accession: SRX20755919  Accession: SRX20755918
Accession: SRX20755917  Accession: SRX20755916
Accession: SRX20755915  Accession: SRX20755914
Accession: SRX20755913  Accession: SRX20755912
Accession: SRX20755911  Accession: SRX20755910
Accession: SRX20755909  Accession: SRX20755908
Accession: SRX20755907  Accession: SRX20755906
Accession: SRX20755905  Accession: SRX20755904
Accession: SRX20755903  Accession: SRX20755902

Residos hospitalarios

Accession: SRX13142947  Accession: SRX13142946
Accession: SRX13142945  

MOSA UASB

Accession: SRX13142944  Accession: SRX13142944
Accession: SRX13142942

activated sludge metagenome

Accession: SRX11245213  Accession: SRX11245212
Accession: SRX11245211

shotgun sequencing for microalgae-bacteria aggregates: antibiotic resistance

Accession: SRX20697646  Accession: SRX20697645
Accession: SRX20697644  Accession: SRX20697643
Accession: SRX20697642  Accession: SRX20697641
Accession: SRX20697640

WGS of human child gut

Accession: SRX20466401  Accession: SRX20466400
Accession: SRX20466399  Accession: SRX20466398
Accession: SRX20466397  Accession: SRX20466396
Accession: SRX20466395  Accession: SRX20466394
Accession: SRX20466393  Accession: SRX20466392
Accession: SRX20466391  Accession: SRX20466390
Accession: SRX20466389  Accession: SRX20466388
Accession: SRX20466387  Accession: SRX20466386
Accession: SRX20466385  Accession: SRX20466384
Accession: SRX20466383  Accession: SRX20466382
Accession: SRX20466381  Accession: SRX20466380
Accession: SRX20466379  Accession: SRX20466378
Accession: SRX20466377  Accession: SRX20466376
Accession: SRX20466375  Accession: SRX20466374
Accession: SRX20466373  Accession: SRX20466372
Accession: SRX20466371  Accession: SRX20466370
Accession: SRX20466369  Accession: SRX20466368
Accession: SRX20466367  Accession: SRX20466366
Accession: SRX20466365  Accession: SRX20466364
Accession: SRX20466363  Accession: SRX20466362

freshwater sediment metagenome

Accession: SRX21391458  Accession: SRX21391457
Accession: SRX21391456  Accession: SRX21391455
Accession: SRX21391454  Accession: SRX21391453
Accession: SRX21391452  Accession: SRX21391451
Accession: SRX21391450  Accession: SRX21391449
Accession: SRX21391448  Accession: SRX21391447
Accession: SRX21391446  Accession: SRX21391445
Accession: SRX21391444  Accession: SRX21391443
Accession: SRX21391442  Accession: SRX21391441

## Control de calidad de los reads
Es el primer paso en el flujo de trabajo en un analisis metagenomico el cual tiene por objetivo evaluar la calidad de todos los reads de las secuencias.
Para realizar el control de calidad de las secuencias, utilizaremos la herramienta FastQC.
```
https://www.bioinformatics.babraham.ac.uk/projects/fastqc/
```
La evaluación y visualización de los parametros de calidad seran ejecutadas mediante el siguiente comando:
``` bash

fastqc read1.fastq.gz read2.fastq.gz 
```
## Trimming
El trimming consiste en la remosion de los adaptadores y reads de baja calidad; este se realiza mediante programas bioinformáticos especiales para esta tarea.
Para este fin instalaremos el programa TrimGalore.
```
https://github.com/FelixKrueger/TrimGalore
```
Para la realizar el proceso de trimming, configuraremos el programa para secuencias de illumina, paired y control de calidad de la salida.
``` bash

trim_galore --paired --fastqc --illumina read1.fastq.gz read2.fastq.gz
```
## Taxonomía basada en reads
Identificación y cuantificación de las especies en una muestra metagenómica determinada basada en la distribución y secuencia de todos los reads.
Para este proceso crearemos una cuenta en Galaxy.
```
https://usegalaxy.org/
```
Y submitiremos los archivos read1 y read2 posterior al trimming. A continuación ejecutaremos la herramienta Kraken2 con los datos cargados.

## Herramientas de viusalización
Para la visualización de la diversidad de la muestra metagenómica, ejecutaremos la herramienta Krona pie chart en Galaxy con los datos de salida del paso anterior.

## Ensamblaje de metagenomas
Es el proceso de descifrar y reconstruir la secuencia de todos los genomas correspondientes a una muestra a partir de pequeños fragmentos de ADN haciendo uso de algoritmos informaticos. 
Con este fin instalaremos la herramienta MEGAHIT.
```
https://github.com/voutcn/megahit
```
Y ejecutaremos el siguiente codigo
``` bash

megahit -1 read1.fastq.gz -2 read2.fastq.gz -o out 
```

## Control de calidad del metagenoma
Consiste en evaluar la calidad del metagenoma ensamblado previamente basándose principalmente en alineamientos con referencias cercanas.
Para este fin instalaremos y ejecutaremos la herramienta metaquast.
```
https://github.com/ablab/quast
```
Y ejecutaremos el siguiente codigo
``` bash

metaquast.py contigs.fasta -o contigs_metaquast
```

## Predicción de genes
La predicción de genes consiste en identificar regiones codificantes en una secuencia de ADN. Al tratarse de un metagenoma, existe una alta posibilidad de encontrar fragmentos de genes.
Para esta tarea, haremos uso del sitio weg MetaGene donde submitiremos el metagenoma ensamblado.
```
http://metagene.nig.ac.jp/metagene/metagene.html
```

## Bases de datos
Para el análisis de los genes obtenidos es importante compararlos con una base de datos de referencia.
Las mas comunes son:

RefSeq: NCBI Reference Sequence Database
```
https://www.ncbi.nlm.nih.gov/refseq/
```
Uniprot
```
https://www.uniprot.org/
```
CAZy
```
http://www.cazy.org/
```
Interpro
```
https://www.ebi.ac.uk/interpro/
```
CARD
```
https://card.mcmaster.ca/
```
