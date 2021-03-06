FROM jupyter/base-notebook:bce63822c5fb

LABEL maintainer="Facundo Rodriguez <facundo@metacell.us>"

ENV USER=$NB_UID \
    ANTPATH=$HOME/ants/bin \
    PATH=$HOME/ants/bin:$PATH
  
ENV ANTPY_GIT=git+https://github.com/ANTsX/ANTsPy.git \
  DCM2NIIX_HTTP=https://github.com/rordenlab/dcm2niix/releases/download/v1.0.20190410/dcm2niix_11-Apr-2019_lnx.zip

ARG DEBIAN_FRONTEND=noninteractive

USER root
RUN apt-get update && apt-get install &&\
    apt-get -y install --no-install-recommends \
      apt-utils \
      bsdtar \
      build-essential \
      ca-certificates \
      cmake \
      cmake-curses-gui \
      curl \
      dcm2niix \
      dicomnifti \
      gfortran-5 \
      git \
      libatlas-base-dev \
      libjpeg62 \
      libxml2-dev \
      libxslt1-dev \
      locales \
      tcsh \
      wget \
      xdot \
      zlib1g-dev &&\
    rm -rf /var/lib/apt/lists/*

USER $NB_UID
RUN \
  conda config --add channels conda-forge &&\
  conda install \
    cycler \
    cython \
    pydicom \
    freetype \
    jpeg \
    libpng \
    matplotlib \
    networkx \
    nibabel \
    numpy \
    openblas \
    pandas \
    patsy \
    pip \
    pillow \
    pyparsing \
    python-dateutil \
    pytz \
    scikit-image \
    scikit-learn \
    scipy \
    scipy \
    setuptools \
    six \
    statsmodels &&\
  conda clean -tipsy


CMD ["jupyter", "notebook", "--NotebookApp.token=''"]