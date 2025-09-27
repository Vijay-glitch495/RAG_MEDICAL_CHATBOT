# Use the Jenkins image as the base image
FROM jenkins/jenkins:lts

# Switch to root user to install dependencies
USER root

# Install prerequisites and Docker
RUN apt-get update -y && \
    apt-get install -y apt-transport-https ca-certificates curl gnupg software-properties-common && \
    curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - && \
    echo "deb [arch=amd64] https://download.docker.com/linux/debian bullseye stable" > /etc/apt/sources.list.d/docker.list && \
    apt-get update -y && \
    apt-get install -y docker-ce docker-ce-cli containerd.io && \
    apt-get clean

# Add Jenkins user to the Docker group (create if it doesn't exist)
RUN groupadd -f docker && \
    usermod -aG docker jenkins

# Create the Docker directory and volume for DinD
RUN mkdir -p /var/lib/docker
VOLUME /var/lib/docker

# Switch back to the Jenkins user
USER jenkins


# I don't understand what I am doing here. If I don't pull, if I don't push, how can I pull?
# 🔹 Step 1: Pull = Download the Image

# When you run:

# docker pull jenkins/jenkins:lts-jdk17


# 👉 You are downloading the Jenkins image (prebuilt by the Jenkins community) from Docker Hub to your computer.

# You don’t need to push anything, because you’re just a consumer.

# Push is only needed if you build a new image and want to share it.