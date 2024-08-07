# Use Ubuntu 20.04 as the base image
FROM ubuntu:20.04

# Metadata labels
LABEL maintainer="abhilesh7@gmail.com"
LABEL version="1.0"
LABEL description="Docker image for PoolSNP"
LABEL org.opencontainers.image.authors="Abhilesh Dhawanjewar <abhilesh7@gmail.com>"

# Set the working directory in the container
WORKDIR /usr/src/app

ENV DEBIAN_FRONTEND=noninteractive
# Install bash (Ubuntu should already have it, but just in case)
RUN apt-get update && apt-get install -y \
    bash \
    git \
    python3 \
    python3-pip \
    parallel \
    && rm -rf /var/lib/apt/lists/*

# Get the latest version of PoolSNP from GitHub
RUN git clone https://github.com/capoony/PoolSNP.git

RUN mv PoolSNP/* . && rm -rf PoolSNP

RUN chmod +x PoolSNP.sh

# Add /usr/src/app to the PATH
ENV PATH="/usr/src/app:${PATH}"

# Adjust permissions to ensure the directory is accessible and writable by any user
# This is important when running with a user specified by UID and GID at runtime
RUN chmod -R 777 /usr/src/app

CMD ["PoolSNP.sh"]