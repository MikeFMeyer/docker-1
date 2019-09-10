FROM debian

RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get install -y curl
RUN apt-get install -y bzip2

EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 1001
EXPOSE 41144

RUN adduser --disabled-login teamspeak
RUN curl http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 > teamspeak-server.tar.bz2
RUN tar -xjvf teamspeak-server.tar.bz2
RUN cp -r teamspeak3-server_linux_amd64/* /home/teamspeak/
COPY ts3server.ini /home/teamspeak
WORKDIR /home/teamspeak
RUN touch .ts3server_license_accepted

ENTRYPOINT ["sh", "ts3server_minimal_runscript.sh", "inifile=ts3server.ini"]
