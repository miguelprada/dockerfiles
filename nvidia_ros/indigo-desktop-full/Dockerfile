FROM miguelprada/nvidia_ros:indigo-desktop

RUN apt-get update -qq \
    && apt-get -qq install --no-install-recommends -y \
        ros-$ROS_DISTRO-desktop-full \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
