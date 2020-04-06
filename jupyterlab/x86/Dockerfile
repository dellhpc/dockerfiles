FROM jupyter/base-notebook:lab-1.0.1

ARG  JUPYTERHUB_VERSION=0.9.6

USER root
ENV  DEBIAN_FRONTEND noninteractive
RUN  apt-get update \
     && apt-get install --yes --no-install-recommends git \
     && rm -rf /var/lib/apt/lists/*
RUN  python -m pip install nbgitpuller \
     $(bash -c 'if [[ $JUPYTERHUB_VERSION == "git"* ]]; then \
        echo ${JUPYTERHUB_VERSION}; \
      else \
        echo jupyterhub==${JUPYTERHUB_VERSION}; \
      fi') \
     && jupyter serverextension enable --py nbgitpuller --sys-prefix
ENV  NBGITPULLER_APP=lab

USER jovyan
#RUN  conda update --quiet --yes -n base conda && \
RUN  conda install --quiet --yes tensorflow pytorch && \ 
     conda clean --all -f -y && \
     pip install --upgrade jupyter-tensorboard jupyterlab-git && \
     jupyter tensorboard enable && \
     jupyter labextension install jupyterlab_tensorboard && \
     jupyter lab build
