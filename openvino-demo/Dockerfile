FROM keichi/openvino

SHELL ["/bin/bash", "-c"]

RUN source /opt/intel/openvino/bin/setupvars.sh && \
    mkdir build && cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release \
          -DCMAKE_CXX_FLAGS="-march=armv7-a" \
          /opt/intel/openvino/deployment_tools/inference_engine/samples && \
    make
RUN cd build && \
    wget --no-check-certificate https://download.01.org/opencv/2019/open_model_zoo/R1/models_bin/face-detection-adas-0001/FP16/face-detection-adas-0001.bin && \
    wget --no-check-certificate https://download.01.org/opencv/2019/open_model_zoo/R1/models_bin/face-detection-adas-0001/FP16/face-detection-adas-0001.xml && \
    wget https://www.dropbox.com/s/ant0eh1q7h6y2jc/Lenna.bmp

CMD source /opt/intel/openvino/bin/setupvars.sh && \
    cd build && \
    ./armv7l/Release/object_detection_sample_ssd -m face-detection-adas-0001.xml -d MYRIAD -i Lenna.bmp
