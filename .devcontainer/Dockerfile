# Use the official Ubuntu image from the Docker Hub
FROM ubuntu:22.04

# Prevent interactive prompts during package installation
ARG DEBIAN_FRONTEND=noninteractive

# Update and install necessary packages
RUN apt-get update && apt-get install -y \
    software-properties-common \
    && add-apt-repository --yes --update ppa:ansible/ansible \
    && apt-get install -y ansible sudo \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Create a non-root user and grant sudo permissions
RUN useradd -m -s /bin/bash vscode && echo "vscode ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Set the working directory
WORKDIR /workspace

# Switch to the non-root user
USER vscode

# Set the default command to bash, so the container starts with it
CMD ["bash"]
