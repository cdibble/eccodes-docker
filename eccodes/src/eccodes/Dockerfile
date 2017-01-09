FROM ubuntu:latest
MAINTAINER kilobike

RUN apt-get update \
&&  apt-get -y install \
    wget \
    git \
    gcc \
    cmake \
    gfortran \
    libopenjpeg-dev \
    libpng-dev \
    libnetcdf-dev \
    python \
    python-tables \
    hdf5-tools \
    libhdf5-dev \
    libhdf5-serial-dev\
    python-numpy \
    python-netcdf4 \
    python-pip \
    && apt-get clean \
    && pip --no-cache-dir install --upgrade pip \
    && pip --no-cache-dir install numpy netcdf4

RUN mkdir eccodes \
    && cd eccodes \
    && mkdir build \
    && cd build \
    && wget -O eccodes_test_data.tar.gz  "http://download.ecmwf.org/test-data/grib_api/eccodes_test_data.tar.gz" \
    && tar -xzf eccodes_test_data.tar.gz \
    && rm eccodes_test_data.tar.gz \
    && cd /eccodes \
    && wget -O eccodes.tar.gz "https://software.ecmwf.int/wiki/download/attachments/45757960/eccodes-2.0.2-Source.tar.gz?api=v2" \
    && tar -xzf eccodes.tar.gz \
    && cd build \
    && pwd \
    && cmake -DCMAKE_INSTALL_PREFIX=/usr/local/eccodes -DENABLE_MEMFS=ON -DENABLE_PNG=ON ../eccodes-2.0.2-Source \
    && make \
    && ctest \
    && make install \
    && pwd \
    && rm -rf /eccodes


CMD ["/bin/bash"]