FROM ubuntu:20.04

# Initialize the image
# Modify to pre-install dev tools and ROCm packages
ARG ROCM_VERSION=6.2
ARG AMDGPU_VERSION=6.2

ENV PATH="${PATH}:/opt/rocm/bin" \
    DEBIAN_FRONTEND=noninteractive

RUN sed -i 's@//.*archive.ubuntu.com@//mirrors.ustc.edu.cn@g' /etc/apt/sources.list.d/ubuntu.sources && \
    apt-get update && apt-get install -y --no-install-recommends ca-certificates curl gnupg2 && \
    curl -sL http://repo.radeon.com/rocm/rocm.gpg.key | apt-key add - && \
    sh -c 'echo deb [arch=amd64] http://repo.radeon.com/rocm/apt/$ROCM_VERSION/ focal main > /etc/apt/sources.list.d/rocm.list' && \
    sh -c 'echo deb [arch=amd64] https://repo.radeon.com/amdgpu/$AMDGPU_VERSION/ubuntu focal main > /etc/apt/sources.list.d/amdgpu.list' && \
    apt-get update &&  apt-get install -y --no-install-recommends rocm && \
    apt-get clean && rm -rf /var/lib/apt/lists/*
