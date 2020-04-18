FROM ubuntu:bionic
ARG DEBIAN_FRONTEND=noninteractive

# Download OpenCV Dependencies
RUN apt-get update && apt-get -y install build-essential cmake \
    git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev \
    libswscale-dev python3.5 python3-numpy libtbb2 libtbb-dev \
    libjpeg-dev libpng-dev libtiff5-dev libdc1394-22-dev \
    libeigen3-dev libtheora-dev libvorbis-dev libxvidcore-dev \
    libx264-dev sphinx-common libtbb-dev yasm libfaac-dev libopencore-amrnb-dev \
    libopencore-amrwb-dev libopenexr-dev libgstreamer-plugins-base1.0-dev \
    libavutil-dev libavfilter-dev libavresample-dev

WORKDIR /opt

# Git clone OpenCV and checkout tag 3.3.1
RUN git clone https://github.com/opencv/opencv.git && cd opencv \
    git checkout tags/3.3.1 -b opcv-3.3.1

# Git clone OpenCV-Contrib and checkout 3.3.1
RUN git clone https://github.com/opencv/opencv_contrib.git && \
    cd opencv_contrib && git checkout tags/3.3.1 -b opcv-contrib-3.3.1

# Build and make OpenCV
RUN cd opencv && mkdir build && cd build && \
    cmake .. && make -j8 && make install


