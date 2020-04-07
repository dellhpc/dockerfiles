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
RUN  pip install --upgrade jupyterlab-git && \
     jupyter lab build
