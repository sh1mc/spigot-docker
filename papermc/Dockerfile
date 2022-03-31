FROM alpine:latest

LABEL maintainer="sh1mc"

ARG MINECRAFT_VERSION

RUN echo "@community http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories
RUN apk update && \
	apk upgrade && \
	apk add --no-cache openjdk17@community git

RUN mkdir /paper && \
	cd /paper && \
	wget "https://papermc.io/api/v2/projects/paper/versions/1.18.1/builds/71/downloads/paper-1.18.1-71.jar"
	
WORKDIR /paper

RUN mv *.jar paper.jar && \
	echo "eula=TRUE" > eula.txt

CMD java -Xms4G -Xmx4G -XX:+UseG1GC -jar paper.jar nogui
