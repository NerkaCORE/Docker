FROM debian:9.3

# Download everything from the repo

RUN apt-get -y update && \
	apt-get -y upgrade && \
	apt-get -y install wget  && \
	apt-get -y install bzip2 && \
	mkdir -p /opt/teamspeak && \
	useradd teamspeak

# Install TeamSpeak3 and add the scripts

RUN wget http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 && \
	tar -vxjf teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 && \
	mv teamspeak3-server_linux_amd64 /opt/teamspeak && \
	rm -rf teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2

WORKDIR /opt/teamspeak/teamspeak3-server_linux_amd64

# /start runs it

RUN		mkdir /data

USER	teamspeak

VOLUME	["/data"]

EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011

ENTRYPOINT ["sh", "ts3server_minimal_runscript.sh"]
