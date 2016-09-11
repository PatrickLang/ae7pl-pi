


## direwolf

This is a native build environment for WB0OSZ's DireWolf. For the latest info, see [github](https://github.com/wb2osz/direwolf)

It will bring up a container based on resin/raspbian, install the needed tools to build, as well as grab the latest source.

### Build environment & code compilation
First, set up & run the build environment


```

docker build -t patricklang/ae7pl-direwolf-build direwolf-build
```

Now run it to actually build direwolf
```
mkdir direwolf-share
docker run -v $PWD/direwolf-share:/direwolf-share patricklang/ae7pl-direwolf-build
```

Outputs will be put into the shared volume, where they can easily be consumed in the next step [direwolf](../docker-direwolf)

### Creating the 'run' container

This will copy the built binary from the previous step, and build a minimal Docker container including it

```
docker build -t patricklang/ae7pl-direwolf -f direwolf-run/Dockerfile .
```

### Running direwolf in a container

The device must be passed with `docker run --device`.



If you only have one USB serial device (such as the ThumbDV) plugged in - it is `/dev/ttyUSB0`. baudrate defaults to 460800 [as used by ThumbDV Model A](http://nwdigitalradio.com/thumbdv-model-a/), but can be overrridden with `--env baudrate=<rate>`


```
docker run --device=/dev/ttyUSB0 -d -p 2460:2460/udp patricklang/ae7pl-direwolf
```