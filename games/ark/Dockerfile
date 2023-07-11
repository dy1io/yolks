FROM        --platform=$TARGETOS/$TARGETARCH debian:stable-slim

## Update base packages and install dependencies
ENV         DEBIAN_FRONTEND=noninteractive
RUN         dpkg --add-architecture i386 \
            && apt-get update \
            && apt-get upgrade -y \
            && apt-get install -y \
                perl-modules \
                curl \
                lsof \
                libc6-i386 \
                lib32gcc1 \
                bzip2

## Configure locale
RUN         update-locale lang=en_US.UTF-8 \
            && dpkg-reconfigure --frontend noninteractive locales

## Setup user and working directory
RUN         useradd -m -d /home/container -s /bin/bash container
USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container
