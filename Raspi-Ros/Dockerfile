FROM debian:stretch-20190910
ENV DEBIAN_FRONTEND noninteractive
# WORKDIR /home/pi
RUN /bin/bash -c "export DEBIAN_FRONTEND='noninteractive'"

# Update and Upgrade
RUN apt -y update && apt-get install -y \
    apt-utils gnupg dirmngr git cmake vim \
    dpkg lsb-release

# install ROS
# RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu  main contrib non-free" > /etc/apt/sources.list.d/ros-latest.list'
RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main contrib non-free" > /etc/apt/sources.list.d/ros-latest.list'
RUN apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654

RUN apt -y update && apt -y upgrade

# Install Python Libraries
RUN apt-get update && apt-get install -y \
    python-catkin-pkg python-rospkg python-rosdistro \
    python3-dev python3-pip python3-testresources \
    python-rosdep python-rosinstall-generator \
    python-wstool python-rosinstall build-essential \
    apt-utils cmake git checkinstall \
    pkg-config dirmngr

RUN pip3 install -U pip numpy

# Installs a debian ros version
RUN rosdep init && rosdep update
RUN apt-get install -y ros-melodic-desktop-full

RUN mkdir -p home/pi/catkin_ws/src

WORKDIR /home/pi/catkin_ws

RUN echo "source /opt/ros/melodic/setup.bash" > ~/.bashrc