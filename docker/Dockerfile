FROM ubuntu:jammy

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y tzdata && \
  apt-get install -y \
  sudo \
  unzip \
  cmake \
  build-essential \
  git \
  vim \
  libjpeg-dev \
  libpng-dev \
  libtiff-dev \
  python3 \
  python3-pip; \
  apt-get autoclean && \
  apt-get clean && \
  pip3 install pyyaml gitpython

RUN git clone https://github.com/changh95/3d_pose_viewer.git && \
    cd 3d_pose_viewer &&\
    python3 ./build_dependencies.py &&\
    mkdir build && cd build && \
    cmake -GNinja ../ && \
    ninja


