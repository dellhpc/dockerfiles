FROM dellhpc/jupyterlab-base:1.0 

RUN  conda install --quiet --yes tensorflow pytorch-cpu && \ 
     conda clean --all -f -y && \
     pip install -U jupyter-tensorboard && \
     jupyter tensorboard enable && \
     jupyter labextension install jupyterlab_tensorboard && \
     jupyter lab build
