# Panda Arm - Franka Emika
This repository contains the application code used to communicate with the Franka Emika arm from Drake. 

## Building the driver

To build, run `bazel build //...`.  This will output two versions of
the driver: `bazel-bin/franka-driver/panda_driver_v4` and
`bazel-bin/franka-driver/panda_driver_v5`.

## Links

* [Website](https://www.franka.de/technology)
* [Franka Control Interface (FCI) Documentation](https://frankaemika.github.io/docs/)
* [`libfranka` API Docs](https://frankaemika.github.io/libfranka/)
* [Panda datasheet](https://s3-eu-central-1.amazonaws.com/franka-de-uploads/uploads/Datasheet-EN.pdf)

## Notes

* Be sure to read the manual, FCI docs, etc.
    * The FCI docs have excellent instructions for getting your network
    interface on Ubuntu set up.
* There are two very distinct versions of Pandas: the FE3 (older) and FR3 (newer)
* There are three version to think about: firmware on the robot (we use
`v4.x`, and `v5.x`) and `libfranka` driver software on the host PC
(`0.8.0` for `v4.x` FE3, and `0.10.0` for `v5.x` FR3).
    * You should see suffixes like `_v4` and `_v5` for relevant
    libraries and binaries. Be sure to coordinate those, e.g. in each station's
    PMD files.
    * If you use the wrong driver, you should get an error like:

            terminate called after throwing an instance of 'franka::IncompatibleVersionException'
            what():  libfranka: Incompatible library version (server version: 4, library version: 5). Please check https://frankaemika.github.io for Panda system updates or use a different version of libfranka.

