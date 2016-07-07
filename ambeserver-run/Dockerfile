FROM resin/rpi-raspbian
ADD ambeserver-share/AMBEServer /usr/bin/AMBEServer

ENV serialport=/dev/ttyUSB0
ENV baudrate=230400
CMD /usr/bin/AMBEserver -d -i $serialport -s $baudrate
