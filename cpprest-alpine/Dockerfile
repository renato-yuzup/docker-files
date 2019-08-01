# Alpine Linux based-image
FROM alpine:latest

# Define which image type we are building.
# Acceptable values: Debug/Release
ARG type=Debug
ARG build_as_shared_lib=1

# Add common tools and packages required by C++ REST API projects
RUN apk add g++ git boost-dev openssl libressl-dev \
    ninja cmake make zlib-dev

# Build and install Websocketpp
RUN git clone git://github.com/zaphoyd/websocketpp.git && \
    cd websocketpp && \
    cmake . && \
    make install && \
    cd .. && \
    rm -rf websocketpp

# Build and install C++ REST SDK
RUN git clone https://github.com/Microsoft/cpprestsdk.git cpprestsdk && \
    cd cpprestsdk && \
    mkdir build && \
    cd build && \
    cmake -G Ninja .. -DCMAKE_BUILD_TYPE=${type} -DBUILD_SHARED_LIBS=${build_as_shared_lib} && \
    ninja && \
    ninja install && \
    cd ../.. && \
    rm -rf cpprestsdk




