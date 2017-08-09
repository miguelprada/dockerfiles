FROM miguelprada/libfreenect2

RUN apt-get update -qq && apt-get install -y -qq \
  python-catkin-tools

WORKDIR /root/ws

RUN mkdir src && cd src && git clone https://github.com/code-iai/iai_kinect2.git

RUN rosdep update && rosdep install --from-paths src -iy

RUN catkin config --extend /opt/ros/$ROS_DISTRO --install --install-space /opt/ros/$ROS_DISTRO && catkin build
