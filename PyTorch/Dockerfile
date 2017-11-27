FROM nvidia/cuda:8.0-cudnn6-devel-ubuntu16.04	
FROM pytorch/pytorch:latest
MAINTAINER Negar Rostamzadeh <negar.rostamzadeh@gmail.com>

# Install some packages I need
RUN apt-get update && apt-get install -y \
    vim \
    python-pip \
    ssh \
    git

# Upgrade pip
RUN pip install --upgrade pip

# Install pytorch for pyton 2.7
RUN pip install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp27-cp27mu-manylinux1_x86_64.whl
RUN pip install torchvision

# Install some python dependences I need in my project
RUN pip install \
    matplotlib \
    plotly \
    dominate \
    future \
    scipy numpy six cycler pytz subprocess32 python-dateutil backports.functools-lru-cache pyparsing olefile Pillow decorator networkx PyWavelets scikit-image pandas seaborn

CMD [“/bin/bash”]
