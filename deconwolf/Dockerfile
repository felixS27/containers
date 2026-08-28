# Stage 1: Build
FROM nvidia/cuda:12.8.1-devel-ubuntu24.04 AS builder

# Set environment variables to prevent interactive prompts
ENV DEBIAN_FRONTEND=noninteractive

# Install required packages and dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    cmake \
    git \
    libfftw3-dev \
    libtiff-dev \
    libgsl-dev \
    libpng-dev \
    ocl-icd-opencl-dev \
    clinfo \
    nvidia-opencl-dev \
    && rm -rf /var/lib/apt/lists/*

# Pin to a specific commit on the dev branch for reproducibility
ARG DECONWOLF_COMMIT=1768629b86dfa0190f587cb46b3e7ad0738a195b

# Clone the deconwolf repository
RUN git clone https://github.com/elgw/deconwolf.git /deconwolf \
    && cd /deconwolf \
    && git checkout ${DECONWOLF_COMMIT}

# Create a build directory
WORKDIR /deconwolf/builddir

# Configure and build deconwolf with OpenCL support
RUN cmake .. && cmake --build .

# Remove unnecessary build dependencies
RUN apt-get purge -y \
    build-essential \
    cmake \
    git \
    && rm -rf /var/lib/apt/lists/* 

# Stage 2: Runtime
FROM nvidia/cuda:12.8.1-base-ubuntu24.04

LABEL org.opencontainers.image.source="https://github.com/felixS27/containers"

ENV DEBIAN_FRONTEND=noninteractive

# Install necessary runtime libraries
RUN apt-get update && apt-get install -y \
libfftw3-dev \
libtiff-dev \
libgsl-dev \
libpng-dev \
libffi-dev \
libssl-dev \
ocl-icd-libopencl1 \
clinfo \
nvidia-opencl-dev \
&& rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# ---------- deconwolf ----------
COPY --from=builder /deconwolf/builddir/src /usr/local/lib/
RUN find /usr/local/lib -name "*.so*" -exec mv -t /usr/local/lib {} \; \
&& ldconfig

COPY --from=builder /deconwolf/builddir/dw /usr/local/bin/dw
COPY --from=builder /deconwolf/builddir/dw_bw /usr/local/bin/dw_bw

WORKDIR /data/