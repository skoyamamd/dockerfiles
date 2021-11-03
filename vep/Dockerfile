FROM ubuntu:20.04

ENV PERL_MM_USE_DEFAULT=1
WORKDIR /opt
ENV PATH="/opt/:${PATH}"

## Installation
RUN \
  apt update && \
  apt install -y build-essential libmysqlclient-dev unzip git libbz2-dev liblzma-dev curl && \
  cpan Archive::Zip && \
  cpan DBD::mysql && \
  cpan DBI && \
  cpan Try::Tiny

RUN \
  curl -L -O https://github.com/Ensembl/ensembl-vep/archive/release/104.zip && \
  unzip 104.zip && \
  cd ensembl-vep-release-104 && \
  perl INSTALL.pl \
  --AUTO acp \
  --NO_HTSLIB \
  --PLUGINS all \
  --SPECIES homo_sapiens \
  --ASSEMBLY GRCh37 && \
  perl INSTALL.pl \
  --AUTO acp \
  --NO_HTSLIB \
  --PLUGINS all \
  --SPECIES homo_sapiens \
  --ASSEMBLY GRCh38

