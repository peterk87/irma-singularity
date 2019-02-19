# IRMA - Singularity container

[![https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg](https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg)](https://singularity-hub.org/collections/2385)

Iterative Refinement Meta-Assembler (IRMA) version 0.6.7 built from [IRMA v0.6.7 zip file] from the [IRMA Website].

## About IRMA

From the [IRMA Website]:

> IRMA was designed for the robust assembly, variant calling, and phasing of highly variable RNA viruses. Currently IRMA is deployed with modules for influenza and ebolavirus. IRMA is free to use and parallelizes computations for both cluster computing and single computer multi-core setups. Please refer to our FAQ below or contact us for further questions. Please read IRMA's full license and disclaimer.

> The [IRMA manuscript] provides more background on the methodology.

> *NOTE: the [SAM] binaries packaged within [LABEL] and the [BLAT] binaries packaged within IRMA may be used for government and/or academic use only. Commercial use and redistribution of [SAM] or [BLAT] is excluded without permission from their authors. Please read the [SAM] license and [BLAT] license.*

## Pre-requisite

Install [Singularity]

## Usage

### Latest version

Run from [Singularity Hub]
```
 singularity run shub://peterk87/irma-singularity
```


The following steps are needed to use the image:

1) Pull the image

```bash
singularity pull --name TMP_DIRECTORY shub://peterk87/irma-singularity@latest
```

This will command will create a file `irma-singularity.simg`, which is executable.

2) Use the image

```bash
./irma-singularity.simg --help
```

### A particular version

```bash
singularity pull --name mlst shub://phgenomics-singularitysistr@VERSION.NUMBER
```

### Suggested pattern

1) Create a singularity folder:

```bash
mkdir HOME/singularity
```

2) Pull the image to the singularity folder.

```bash
singularity pull --name sistr shub://peterk87/irma-singularity@latest
```

3) Link the image to a folder in your `$PATH` (e.g. `$HOME/bin`)

```bash
ln -s $HOME/singularity/irma.simg $HOME/bin/IRMA
```
4) Now, when you login again, you should be able to just type:

```bash
IRMA
```
Output:
```
Welcome to IRMA 0.6.7
IRMA installed on 2019-02-19
Iterative Refinement Meta-Assembler (IRMA), v0.6.7 (13 APR 2017)
Samuel S. Shepard (NCIRD/OID/CDC), vfn4@cdc.gov

GPL version 3. This program comes with ABSOLUTELY NO WARRANTY. This is free software.
You are welcome to redistribute it under certain conditions. See:  <http://www.gnu.org/licenses/>.
Components of this pipeline have non-commercial restrictions. See: IRMA_RES/scripts/packaged-citations-licenses

USAGE:
(PAIRED-END):   IRMA <MODULE|MODULE-CONFIG> <R1.fastq.gz|R1.fastq> <R2.fastq.gz|R2.fastq> <sample_name>
(SINGLE-END):   IRMA <MODULE|MODULE-CONFIG> <fastq|fastq.gz> <sample_name>
```



[Singularity]: https://www.sylabs.io/singularity/
[Singularity Hub]: https://singularity-hub.org/collections/2385/usage
[IRMA manuscript]: https://bmcgenomics.biomedcentral.com/articles/10.1186/s12864-016-3030-6
[IRMA Website]: https://wonder.cdc.gov/amd/flu/irma/
[IRMA v0.6.7 zip file]: https://wonder.cdc.gov/amd/flu/irma/flu-amd-201704.zip
[SAM]: https://www.ncbi.nlm.nih.gov/pubmed/9927713
[BLAT]: http://www.kentinformatics.com/products.html
[LABEL]: https://wonder.cdc.gov/amd/flu/label/
[SSW]: http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0082138
[samtools]: http://www.htslib.org/
[GNU Parallel]: https://www.gnu.org/software/parallel/
[Shogun Toolbox]: http://shogun.ml/
