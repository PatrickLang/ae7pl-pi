FROM resin/rpi-raspbian
RUN apt-get update
RUN apt-get install gcc
RUN apt-get install g++

WORKDIR /ambeserver-build
# For full details, see:
# https://github.com/dl5di/OpenDV

# Building
RUN curl -k https://raw.githubusercontent.com/dl5di/OpenDV/master/DummyRepeater/DV3000/AMBEserver.c -o AMBEServer.c

CMD gcc AMBEServer.c -o AMBEServer