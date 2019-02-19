Bootstrap: docker
From: continuumio/miniconda3:4.5.4

%help
  A Singularity image for IRMA

%labels
  Author Peter Kruczkiewicz
  Build 1.1

%environment
  export VERSION=0.6.7
  export PATH=/opt/conda/bin:/opt/irma:$PATH
  export LC_ALL=C

%post
  apt-get -y update
  apt-get -y install bash wget zip gzip procps
  apt-get clean
  export PATH=/opt/conda/bin:/opt/irma:$PATH
  conda config --add channels defaults
  conda config --add channels conda-forge
  conda config --add channels r
  conda config --add channels bioconda
  conda install -y r-base perl=5.22.2.1 mafft
  conda clean -tipsy
  wget https://wonder.cdc.gov/amd/flu/irma/flu-amd-201704.zip
  unzip flu-amd-201704.zip
  rm flu-amd-201704.zip
  rm flu-amd/LABEL_RES/scripts/binaries_and_licenses/shogun1.1.0_cmdline_static/shogun_linux32
  rm flu-amd/LABEL_RES/scripts/binaries_and_licenses/shogun1.1.0_cmdline_static/shogun_darwin64
  mv flu-amd /opt/irma
  NOW=`date`
  echo "export NOW=\"${NOW}\"" >> $SINGULARITY_ENVIRONMENT
  echo "Done"

%runscript
  echo "IRMA version: $VERSION" >&2
  echo "Container created $NOW"
  exec IRMA "$@"

%test
  export PATH=/opt/conda/bin:/opt/irma:$PATH
  echo "Testing LABEL"
  LABEL /opt/irma/tests/test1.fa label-test H9v2011
  echo "Testing IRMA"
  IRMA FLU /opt/irma/tests/test2.fastq irma-test

echo "Success"
