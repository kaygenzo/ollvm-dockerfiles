FROM gcc:7.3.0

ENV HOME /home/workspace

ARG cmake=https://cmake.org/files/v3.25/cmake-3.25.0-linux-x86_64.tar.gz
ARG cmakeDir=/opt/cmake-3.25

CMD ["/bin/bash"]

RUN mkdir -p ${cmakeDir} && \
    wget -qO- "${cmake}" | tar --strip-components=1 -xz -C ${cmakeDir}

ENV PATH ${cmakeDir}/bin:${PATH}

WORKDIR ${HOME}

RUN git clone https://github.com/qtfreet00/llvm-obfuscator.git && \
    mkdir build && cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release ../llvm-obfuscator/ && \
    make -j7

CMD ["/bin/cp", "-r", "build/bin/", "/ollvm/bin"]
