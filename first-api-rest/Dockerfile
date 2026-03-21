FROM jenkins/jenkins:lts

USER root

RUN apt-get update && \
    apt-get install -y \
        ca-certificates \
        curl \
        gnupg \
        wget \
        maven

USER jenkins