# Pull base image of UBUNTU
FROM ubuntu:latest

# Install Java.
RUN  \
  apt-get -y update && apt-get -y install software-properties-common && \
  echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
  add-apt-repository -y ppa:webupd8team/java && \
  apt-get update && \
  apt-get install -y oracle-java8-installer && \
  rm -rf /var/lib/apt/lists/* && \
  rm -rf /var/cache/oracle-jdk8-installer

# Define working directory.
WORKDIR ./data

# Define commonly used JAVA_HOME variable
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

# Pull base image of NGINX
FROM nginx
COPY ./usr/share/nginx/html /usr/share/nginx/html

USER root

# Install Prerequisites
RUN apt-get -qq -y update && apt-get -qq  -y install curl && apt-get -qq  -y install gpg \
    curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg \
    mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg \
    sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'

RUN apt-get -y install apt-transport-https \
    apt-get -y update \
    apt-get -y install dotnet-sdk-2.1.105
