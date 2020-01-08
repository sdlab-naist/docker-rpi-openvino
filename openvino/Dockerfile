FROM arm32v7/ubuntu:18.04

RUN apt-get update && \
    apt-get install -y wget cmake g++ autoconf libtool
RUN wget https://download.01.org/opencv/2019/openvinotoolkit/R3/l_openvino_toolkit_runtime_raspbian_p_2019.3.334.tgz && \
    mkdir -p /opt/intel/openvino && \
    tar xzvf l_openvino_toolkit_runtime_raspbian_p_2019.3.334.tgz --strip 1 -C /opt/intel/openvino
RUN wget https://github.com/libusb/libusb/archive/v1.0.23.tar.gz && \
    tar xzvf v1.0.23.tar.gz && \
    cd libusb-1.0.23 && \
    ./bootstrap.sh && \
    ./configure --disable-udev --enable-shared  && \
    make -j 4 && \
    make install && \
    ldconfig /usr/local/lib
