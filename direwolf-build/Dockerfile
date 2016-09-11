FROM resin/rpi-raspbian
RUN apt-get update
RUN apt-get upgrade
RUN apt-get install gcc g++ git automake libtool texinfo
RUN apt-get install libasound2-dev

WORKDIR /direwolf-share

RUN cd /direwolf-share & git clone https://github.com/wb2osz/direwolf.git

# Building
CMD make