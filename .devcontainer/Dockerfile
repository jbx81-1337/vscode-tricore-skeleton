FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt -y update
RUN apt -y install yacc bison build-essential git
RUN git clone --recursive https://github.com/EEESlab/tricore-gcc-toolchain-11.3.0.git
RUN apt -y install libgmp-dev libmpc-dev file libtool flex texinfo cmake

WORKDIR /tricore-gcc-toolchain-11.3.0
RUN ./build-toolchain --all

WORKDIR /
RUN cp -R /tricore-gcc-toolchain-11.3.0/INSTALL /tricore-gcc

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME --shell /bin/bash \
    #
    # [Optional] Add sudo support. Omit if you don't need to install software after connecting.
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

USER $USERNAME