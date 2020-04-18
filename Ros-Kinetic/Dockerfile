
# This is an auto generated Dockerfile for ros:desktop
# generated from docker_images/create_ros_image.Dockerfile.em
FROM ros:kinetic-robot-xenial

# install ros packages
RUN apt-get update && apt-get install -y \
    ros-kinetic-desktop=1.3.2-0* \
    && rm -rf /var/lib/apt/lists/*

# install more stuff

RUN apt-get update && apt-get install -y vim

# Make Necessary files
RUN mkdir -p /opt/ros/kinetic/catkin_ws/src
WORKDIR /opt/ros/kinetic/catkin_ws

# Put lines in /.bashrc
RUN echo "source devel/setup.bash;" >> ~/.bashrc
RUN echo "export ROS_HOSTNAME=172.17.0.1" >> ~/.bashrc
RUN echo "export ROS_MASTER_URI=http://172.17.0.1:11311" >> ~/.bashrc

# Runs catkin_make
RUN /bin/bash -c ". /opt/ros/kinetic/setup.bash; catkin_make"





