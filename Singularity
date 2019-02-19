Bootstrap: docker
From: continuumio/miniconda3:4.5.4

%help
A Singularity image for IRMA

%labels
Maintainer Peter Kruczkiewicz
Build 1.0

%environment
  export VERSION=0.6.7
  export PATH=/opt/conda/bin:/opt/irma:$PATH

%post
  apt-get -y update
  apt-get -y install wget zip gzip procps

  export PATH=/opt/conda/bin:/opt/irma:$PATH
  echo "PATH=$PATH"
  conda config --add channels defaults
  conda config --add channels conda-forge
  conda config --add channels r
  conda config --add channels bioconda

  conda install -y r-base perl=5.22.2.1
  
  wget https://wonder.cdc.gov/amd/flu/irma/flu-amd-201704.zip
  unzip flu-amd-201704.zip
  
  mv flu-amd /opt/irma

  echo "IRMA installed on $(date "+%Y-%m-%d")" > /etc/dbupdate
  chmod 555 /etc/dbupdate
  
  echo "Done"

%runscript
  echo "Welcome to IRMA $VERSION" >&2
  cat /etc/dbupdate >&2
  exec IRMA "$@"

%test
  export PATH=/opt/conda/bin:/opt/irma:$PATH
  echo "Testing LABEL"
  LABEL /opt/irma/tests/test1.fa label-test H9v2011
  echo "Testing IRMA"
  IRMA FLU /opt/irma/tests/test2.fastq irma-test

echo "Success"
