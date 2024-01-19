FROM ubuntu:latest 
# update

# Set the time zone to Tokyo
ENV DEBIAN_FRONTEND=noninteractive
ENV TZ Asia/Tokyo

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

# download miniconda package and install miniconda
# archive -> https://repo.anaconda.com/miniconda/
# M1チップApple使いはローカルで動かしたい時こっち
# RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh && \
#     sh /opt/Miniconda3-latest-Linux-aarch64.sh -b -p /opt/miniconda3 && \
#     rm -f Miniconda3-latest-Linux-aarch64.sh

# intelチップor Linux環境に繋ぐときはこっち
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh && \
    sh /opt/Miniconda3-latest-Linux-x86_64.sh -b -p /opt/miniconda3 && \
    rm -f Miniconda3-latest-Linux-x86_64.sh


# set path
ENV PATH /opt/miniconda3/bin:$PATH

RUN pip freeze > /tmp/requirements-base-image.txt
COPY ./requirements.txt /tmp/requirements.txt
RUN pip install -r /tmp/requirements.txt

WORKDIR /
RUN mkdir /work

# execute jupyterlab as a default command
# CMD ["jupyter", "lab", "--ip=0.0.0.0", "--allow-root", "--LabApp.token=''"]
