# ##########################################################################
# File: Dockerfile
# Author: gvatsal60 [Vatsal Gupta]
# Date: 05-Dec-2024
# Description: Brief description of the Dockerfile purpose.
# ##########################################################################

# ##########################################################################
# License
# ##########################################################################
# This Dockerfile is licensed under the MIT License.
# License information should be updated as necessary.
# ##########################################################################

# ##########################################################################
# Base Image
# ##########################################################################
FROM ubuntu:noble AS base

# ##########################################################################
# Maintainer
# ##########################################################################
LABEL maintainer="gvatsal60"

# ##########################################################################
# Install Dependencies
# ##########################################################################
ENV IMG_USR=ubuntu

RUN apt-get update \
  && apt-get -y install --no-install-recommends \
  apt-transport-https \
  apt-utils \
  ca-certificates \
  curl \
  gnupg \
  lsb-release \
  sudo \
  && apt-get -y clean \
  && rm -rf /var/lib/apt/lists/*

ADD https://get.docker.com /tmp/get-docker.sh
RUN sh /tmp/get-docker.sh \
  && rm /tmp/get-docker.sh \
  && usermod -aG docker ${IMG_USR} \
  && systemctl enable docker.service \
  && systemctl enable containerd.service \
  && service docker start

ADD https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 /tmp/minikube
RUN chmod +x /tmp/minikube \
  && install /tmp/minikube /usr/local/bin/ \
  && rm /tmp/minikube \
  && minikube start --driver=docker --force

# ##########################################################################
# Copy Files
# ##########################################################################

# ##########################################################################
# Set Working Directory
# ##########################################################################
WORKDIR /

# ##########################################################################
# Expose Port
# ##########################################################################

# ##########################################################################
# Command to Run
# ##########################################################################
CMD ["tail -F /dev/null"]
