FROM nginx
COPY ./usr/share/nginx/html /usr/share/nginx/html

USER root
RUN apt-get update -y

RUN apt-get install software-properties-common -y
RUN add-apt-repository ppa:webupd8team/java -y
RUN apt-get update -y
