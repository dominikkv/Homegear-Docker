FROM debian:stretch
MAINTAINER Sathya Laufer <sathya@homegear.email>
RUN apt-get update && apt-get -y install apt-transport-https wget ca-certificates apt-utils gnupg
RUN wget https://homegear.eu/packages/Release.key && apt-key add Release.key && rm Release.key
RUN echo 'deb https://homegear.eu/packages/Debian/ stretch/' >> /etc/apt/sources.list.d/homegear.list
RUN apt-get update && apt-get -y install libhomegear-node homegear homegear-nodes-core homegear-nodes-extra homegear-homematicbidcos homegear-homematicwired homegear-insteon homegear-max homegear-philipshue homegear-sonos homegear-kodi homegear-ipcam homegear-beckhoff homegear-knx homegear-enocean homegear-intertechno homegear-influxdb
RUN rm -f /etc/homegear/dh1024.pem
RUN rm -f /etc/homegear/homegear.crt
RUN rm -f /etc/homegear/homegear.key
RUN cp -R /etc/homegear /etc/homegear.config
RUN cp -R /var/lib/homegear /var/lib/homegear.data
# Inspired by Dockerfile from visevision
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

VOLUME ["/etc/homegear", "/var/lib/homegear", "/var/log/homegear"]

COPY start.sh /start.sh
RUN chmod +x /start.sh
CMD /start.sh

EXPOSE 2001 2002 2003
