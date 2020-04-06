FROM jupyter/base-notebook:lab-1.0.4 

RUN conda update --quiet --yes -n base conda
    conda install --quiet --yes \
    tensorflow-gpu=1.14.0 && \
    conda clean --all -f -y

RUN conda install --quiet --yes jupyterlab=1.1.1

RUN pip install jupyter-tensorboard==0.1.10 && \
    jupyter tensorboard enable && \
    jupyter labextension install jupyterlab_tensorboard

RUN jupyter labextension install @jupyterlab/git && \
    pip install --upgrade jupyterlab-git==0.8.1 && \
    jupyter serverextension enable --py jupyterlab_git && \
    jupyter lab build

RUN conda install --quiet --yes -c r r=3.6.0 r-irkernel=0.8.15
