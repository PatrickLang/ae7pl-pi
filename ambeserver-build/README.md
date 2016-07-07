


## AMBEServer

This is a native build environment for G4KLX's AMBEServer. For the latest info, see [github](https://github.com/dl5di/OpenDV/tree/master/DummyRepeater/DV3000), or the [PCRepeaterController yahoo group](https://groups.yahoo.com/neo/groups/pcrepeatercontroller/info)

It will bring up a container based on resin/raspbian, install the needed tools to build, as well as grab the latest source.

### Build environment & code compilation
First, set up & run the build environment


```

docker build -t patricklang/ae7pl-ambeserver-build  ambeserver-build
```

Now run it to actually build AMBEServer
```
mkdir ambeserver-share
docker run -v ./ambeserver-share:/ambeserver-share patricklang/ae7pl-ambeserver-build
```

Outputs will be put into the shared volume, where they can easily be consumed in the next step [ambeserver](../docker-ambeserver)

### Creating the 'run' container

This will copy the built binary from the previous step, and build a minimal Docker container including it

```
docker build -t patricklang/ae7pl-ambeserver ambeserver-run
```

### Running AMBEServer in a container


> TODO serial & network port forward missing

```
docker run patricklang/ae7pl-ambeserver
```