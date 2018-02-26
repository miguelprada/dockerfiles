FROM nvidia/cuda:8.0-runtime-ubuntu14.04

ENV ROS_DISTRO indigo
ENV OS_CODE_NAME trusty

RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

RUN apt-get update -qq \
    && apt-get -qq install --no-install-recommends -y apt-utils gnupg wget ca-certificates sudo

RUN echo "deb http://packages.ros.org/ros/ubuntu ${OS_CODE_NAME} main" > /etc/apt/sources.list.d/ros-latest.list

RUN apt-key adv --keyserver http://packages.ros.org/ros/ubuntu --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116 \
    || { wget "https://raw.githubusercontent.com/ros/rosdistro/master/ros.key" -O - | sudo apt-key add -; }

RUN sed -i "/^# deb.*multiverse/ s/^# //" /etc/apt/sources.list \
    && apt-get update -qq \
    && apt-get -qq install --no-install-recommends -y \
        build-essential \
        python-catkin-tools \
        python-pip \
        python-rosdep \
        python-wstool \
        ros-$ROS_DISTRO-catkin \
        ssh-client \
        ros-$ROS_DISTRO-ros-base \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

COPY ./ros_entrypoint.sh /

ENTRYPOINT ["/ros_entrypoint.sh"]

CMD ["bash"]
