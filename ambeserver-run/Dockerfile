FROM resin/rpi-raspbian
ADD ambeserver-share/AMBEServer /usr/bin/AMBEServer

ENV serialport=/dev/ttyUSB0
ENV baudrate=460800
EXPOSE 2460/udp
CMD /usr/bin/AMBEServer -i $serialport -s $baudrate
