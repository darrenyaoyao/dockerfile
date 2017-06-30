FROM darrenyaoyao/cuda-torch

MAINTAINER Darren darren.huang@umbocv.com

RUN apt-get update \
    && apt-get -qy dist-upgrade \
    && apt-get -qy install libav-tools

RUN mkdir /opt/opencv-build && cd /opt/opencv-build \
    && git clone https://github.com/Itseez/opencv && cd opencv \
    && git checkout 3.1.0 && mkdir build && cd build \
    && cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local -D CUDA_GENERATION=Auto -D WITH_CUDA=OFF -DPYTHON3_EXECUTABLE=/usr/local/bin/python3 .. \
    && make -j12  && make install && make clean && cd .. \
    && cd / && rm -rf /opt/opencv-build \
    && luarocks install cv


