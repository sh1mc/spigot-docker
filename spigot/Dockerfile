FROM alpine:latest

LABEL maintainer="sh1mc"

ARG MINECRAFT_VERSION

RUN echo "@community http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories
RUN apk update && \
	apk upgrade && \
	apk add --no-cache openjdk16@community git

RUN mkdir /spigot && \
	cd /spigot && \
	wget https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar && \
	java -jar BuildTools.jar --rev ${MINECRAFT_VERSION}
	
WORKDIR /spigot

RUN mv spigot-${MINECRAFT_VERSION}.jar spigot.jar && \
	echo "eula=TRUE" > eula.txt

CMD java -Xms1G -Xmx1G -XX:+UseG1GC -jar spigot.jar nogui
