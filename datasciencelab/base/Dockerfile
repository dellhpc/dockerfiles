FROM jupyter/base-notebook:lab-1.0.1

LABEL org.opencontainers.image.title="Dell Data Science Lab - Base Container" \
      org.opencontainers.image.description="A JupyterLab container with Python3 and R kernels, plus jupyterlab-git extension" \
      org.opencontainers.image.author="Lucas A. Wilson" \
      org.opencontainers.image.vendor="Dell Technologies" \
      org.opencontainers.image.version="1.0" \
      org.opencontainers.image.licenses="Apache-2.0" \
      org.opencontainers.image.source="https://github.com/dellhpc/dockerfiles/datasciencelab/base/Dockerfile" \
      org.opencontainers.image.documentation="https://github.com/dellhpc/dockerfiles/datasciencelab/README.md"

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
RUN  conda install --quiet --yes r r-irkernel && \
     pip install --upgrade jupyterlab-git && \
     jupyter lab build
