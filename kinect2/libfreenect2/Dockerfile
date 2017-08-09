FROM ros:indigo

RUN apt-get -qq update && apt-get install -y -qq \
  build-essential \
  cmake \
  libjpeg-turbo8-dev \
  libturbojpeg \
  pkg-config \
  wget

WORKDIR /root/src/

RUN git clone https://github.com/OpenKinect/libfreenect2.git

RUN cd libfreenect2/depends && ./download_debs_trusty.sh

RUN dpkg -i libfreenect2/depends/debs/libusb*deb

RUN dpkg -i libfreenect2/depends/debs/libglfw3*; apt-get install -f -y -qq && apt-get install -y -qq libgl1-mesa-dri-lts-vivid

RUN mkdir libfreenect2_build && cd libfreenect2_build && cmake ../libfreenect2 -DENABLE_CXX11=ON && make && make install
