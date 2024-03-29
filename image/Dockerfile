FROM ubuntu:22.04

ENV USER=root
ENV HOME=/root

RUN apt update && \
    DEBIAN_FRONTEND=noninteractive apt install -y --no-install-recommends \
    gdb libc6-dbg strace libncurses-dev universal-ctags help2man\
    curl git sudo ca-certificates keyboard-configuration console-setup \
    build-essential cmake perl python3 make autoconf g++ flex bison ccache \
    libgoogle-perftools-dev numactl perl-doc libfl2 libfl-dev zlib1g \
    zlib1g-dev gtkwave libsystemc libsystemc-doc libsystemc-dev iverilog \
    vim bash automake autotools-dev libmpc-dev libmpfr-dev libgmp-dev gawk \
    texinfo gperf libtool patchutils bc libexpat-dev wget libiberty-dev \
    libftdi-dev pkg-config device-tree-compiler googletest locales && \
    rm -rf /var/lib/apt/lists/*

RUN locale-gen en_US.UTF-8

COPY scripts /root/scripts
WORKDIR /root/scripts

RUN for i in do_*.sh; do ./$i; done;

WORKDIR /root
RUN cp scripts/env.sh /root/.env.sh && echo ". /root/.env.sh" >> .bashrc

USER ${USER}
WORKDIR ${HOME}
CMD ["/bin/bash"]
