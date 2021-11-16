FROM alpine:latest

LABEL maintainer="sh1mc"

ARG MINECRAFT_VERSION

RUN echo "@community http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories
RUN apk update && \
	apk upgrade && \
	apk add --no-cache openjdk16@community git

RUN mkdir /paper && \
	cd /paper && \
	wget https://papermc.io/api/v2/projects/paper/versions/1.17.1/builds/384/downloads/paper-1.17.1-384.jar
	
WORKDIR /paper

RUN mv paper-1.17.1-384.jar paper.jar && \
	echo "eula=TRUE" > eula.txt

CMD java -Xms1G -Xmx1G -XX:+UseG1GC -jar paper.jar nogui
