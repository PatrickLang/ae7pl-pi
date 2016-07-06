This is a native build environment for G4KLX's AMBEServer. For the latest info, see [github](https://github.com/dl5di/OpenDV/tree/master/DummyRepeater/DV3000), or the [PCRepeaterController yahoo group](https://groups.yahoo.com/neo/groups/pcrepeatercontroller/info)

It will bring up a container based on resin/raspbian, install the needed tools to build, as well as grab the latest source.

Outputs will be put into the shared volume, where they can easily be consumed in the next step [ambeserver](../docker-ambeserver)