FROM dellhpc/datasciencelab-base:1.0 

LABEL org.opencontainers.image.title="Dell Data Science Lab - CPU Container" \
      org.opencontainers.image.description="A JupyterLab container with CPU-optimized TensorFlow and PyTorch, plus TensorBoard" \
      org.opencontainers.image.author="Lucas A. Wilson" \
      org.opencontainers.image.vendor="Dell Technologies" \
      org.opencontainers.image.version="1.0" \
      org.opencontainers.image.licenses="Apache-2.0" \
      org.opencontainers.image.source="https://github.com/dellhpc/dockerfiles/datasciencelab/cpu/Dockerfile" \
      org.opencontainers.image.documentation="https://github.com/dellhpc/dockerfiles/datasciencelab/README.md"

RUN  conda install --quiet --yes tensorflow pytorch-cpu && \ 
     conda clean --all -f -y && \
     pip install -U jupyter-tensorboard && \
     jupyter tensorboard enable && \
     jupyter labextension install jupyterlab_tensorboard && \
     jupyter lab build
