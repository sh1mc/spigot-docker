FROM alpine:latest

LABEL maintainer="sh1mc"

ARG MINECRAFT_VERSION
ARG EULA_TXT

RUN echo "@testing http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories
RUN apk update && \
	apk upgrade && \
	apk add --no-cache openjdk16@testing git

RUN mkdir /spigot && \
	cd /spigot && \
	wget https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar && \
	java -jar BuildTools.jar --rev ${MINECRAFT_VERSION}
	
WORKDIR /spigot

RUN mv spigot-${MINECRAFT_VERSION}.jar spigot.jar && \
	echo eula=${EULA_TXT} > eula.txt

CMD java -Xms1G -Xmx2G -XX:+UseG1GC -jar spigot.jar nogui
