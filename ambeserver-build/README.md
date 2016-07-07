


## AMBEServer

This is a native build environment for G4KLX's AMBEServer. For the latest info, see [github](https://github.com/dl5di/OpenDV/tree/master/DummyRepeater/DV3000), or the [PCRepeaterController yahoo group](https://groups.yahoo.com/neo/groups/pcrepeatercontroller/info)

Also [NWDR's page](http://nwdigitalradio.com/category/ambeserver/)

It will bring up a container based on resin/raspbian, install the needed tools to build, as well as grab the latest source.

### Build environment & code compilation
First, set up & run the build environment


```

docker build -t patricklang/ae7pl-ambeserver-build  ambeserver-build
```

Now run it to actually build AMBEServer
```
mkdir ambeserver-share
docker run -v $PWD/ambeserver-share:/ambeserver-share patricklang/ae7pl-ambeserver-build
```

Outputs will be put into the shared volume, where they can easily be consumed in the next step [ambeserver](../docker-ambeserver)

### Creating the 'run' container

This will copy the built binary from the previous step, and build a minimal Docker container including it

```
docker build -t patricklang/ae7pl-ambeserver -f ambeserver-run/Dockerfile .
```

### Running AMBEServer in a container

The device must be passed with `docker run --device`.
If you only have one USB serial device (such as the ThumbDV) plugged in - it is `/dev/ttyUSB0`. baudrate defaults to 460800 [as used by ThumbDV Model A](http://nwdigitalradio.com/thumbdv-model-a/), but can be overrridden with `--env baudrate=<rate>`


```
docker run --env serialport=/dev/ttyUSB0 --env baudrate=460800 --device=/dev/ttyUSB0 -d -p 2460:2460/udp patricklang/ae7pl-ambeserver
```