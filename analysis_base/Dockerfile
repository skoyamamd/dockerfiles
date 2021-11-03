FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive 
WORKDIR /root

RUN apt update && \
  apt install -y build-essential python3-dev cmake git vim wget && \
  mkdir -p $HOME/.vim/bundle && cd ~/.vim/bundle && \
  git clone https://github.com/VundleVim/Vundle.vim.git && \
  wget -O $HOME/.vimrc https://raw.githubusercontent.com/skoyamamd/gcp_dotfiles/master/vimrc && \
  vim -c PluginInstall -c qall && \
  cd $HOME/.vim/bundle/YouCompleteMe &&  \
  python3 install.py

RUN cd $HOME && \
  wget --no-check-certificate https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh && \
  bash ~/miniconda.sh -b -p $HOME/miniconda \
  eval "$($HOME/miniconda/bin/conda shell.bash hook)" && conda init
  echo "conda activate test" >> ~/.bashrc
  conda create -n test python=3.7 -y && conda activate test
  conda install -c bioconda -y samtools tabix bedtools bgenix
  conda install -c bioconda -y samtools=1.9 --force-reinstall

RUN mkdir -p $HOME/local/bin \
  wget https://s3.amazonaws.com/plink2-assets/plink2_linux_x86_64_20211011.zip && \
  unzip plink2_linux_x86_64_20211011.zip \
 
