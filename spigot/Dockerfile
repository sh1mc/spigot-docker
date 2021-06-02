FROM alpine:latest

LABEL maintainer="sh1mc"

ARG MINECRAFT_VERSION
ARG EULA_TXT

RUN apk update && \
	apk upgrade && \
	apk add --no-cache openjdk8 git

RUN mkdir /spigot && \
	cd /spigot && \
	wget https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar && \
	java -jar BuildTools.jar --rev ${MINECRAFT_VERSION}
	
WORKDIR /spigot

RUN mv spigot-${MINECRAFT_VERSION}.jar spigot.jar && \
	echo eula=${EULA_TXT} > eula.txt

CMD java -Xms4G -Xmx4G -XX:+UseG1GC -jar spigot.jar nogui
