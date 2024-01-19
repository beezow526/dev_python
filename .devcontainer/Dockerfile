FROM ubuntu:latest 
# update
RUN apt-get -y update && apt-get install -y python3-pip python3-dev \ 
graphviz \
libsm6 \
libxext6 \
libxrender-dev \
libglib2.0-0 \
sudo \
wget \
vim \
git

#install miniconda3
WORKDIR /opt

# download anaconda package and install anaconda
# archive -> https://repo.anaconda.com/archive/
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh && \
    sh /opt/Miniconda3-latest-Linux-aarch64.sh -b -p /opt/anaconda3 && \
    rm -f Miniconda3-latest-Linux-aarch64.sh

# set path
ENV PATH /opt/miniconda3/bin:$PATH

# # Copy requirements.txt to the container
# COPY requiremets.txt /tmp/requiremets.txt

# # Install libraries from requirements.txt
# RUN pip install --upgrade pip && \
#     pip install -r /tmp/requiremets.txt

RUN pip freeze > /tmp/requirements-base-image.txt
COPY ./requirements.txt /tmp/requirements.txt
RUN pip install -r /tmp/requirements.txt

WORKDIR /
RUN mkdir /work

# execute jupyterlab as a default command
# CMD ["jupyter", "lab", "--ip=0.0.0.0", "--allow-root", "--LabApp.token=''"]