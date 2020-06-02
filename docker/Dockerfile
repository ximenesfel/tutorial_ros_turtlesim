FROM ros:melodic-ros-base

RUN apt update \
    && apt install -y qt5-qmake

RUN echo "ROS_DISTRO=melodic " >> /root/.bashrc

RUN echo "source /opt/ros/melodic/setup.bash" >> /root/.bashrc \
    && /bin/bash -c "source /root/.bashrc"

RUN mkdir -p /root/catkin_ws/src
WORKDIR /root/catkin_ws
RUN /bin/bash -c '. /opt/ros/melodic/setup.bash; cd /root/catkin_ws; catkin_make'


RUN apt install -y ros-melodic-turtlesim

WORKDIR /root/