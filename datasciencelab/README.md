# JupyterLab container specs
This directory contains Dockerfiles for the JupyterLab containers offered by Omnia's JupyterHub installation. Container images contain the following:
* Python3 kernel
* R kernel
* Julia kernel
* TensorFlow 2.0.1
* PyTorch 1.4.0
* TensorBoard
* jupyterlab-git
* jupyterlab-tensorboard

## Directories
* `base` - A Base image from which other JupyterLab containers will be constructed
* `x86` - Dockerfile for Intel Xeon CPU nodes (unaccelerated)
* `nvidia` - Dockerfile for Nvidia GPU-accelerated nodes
