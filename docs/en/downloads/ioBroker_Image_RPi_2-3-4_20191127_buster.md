---
translatedFrom: de
translatedWarning: If you want to edit this document please delete "translatedFrom" field, elsewise this document will be translated automatically again
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/en/downloads/ioBroker_Image_RPi_2-3-4_20191127_buster.md
title: ioBroker Image for Raspberry Pi2 / 3/4 Buster 20191127
hash: NpNX09q/cxysJvJptolRsFtxi4rBhgFAkCb+5zdnbJo=
---
# IoBroker Image for Raspberry Pi2 / 3/4 Buster 20191127
## Creating a μ-SD card
This is an SD card image for the Raspberry Pi2, Pi3, Pi3 B + or Pi4.

The image was created on a Raspberry Pi4 with 4GB RAM, but should also run on all mentioned. It is suitable for 8 GB cards and larger. However, a 16 GB is the recommended minimum size.
16GB cards are recommended anyway so that not always the same cells are described.

The image is unpacked and then written to the SD card using the Balena Etcher program. Etcher is available for different operating systems.

## Components of the image
The image contains the Raspbian lite, based on Debian 10 "Buster" from 26.09.2019 after download from http://www.raspberrypi.org/downloads.

In addition, packages that are necessary for some adapters were installed.

The following user is created:

* User: `pi`,
* Password: `raspberry`

Node-js is installed in the version 10.17.0 and of course iobroker over the installer with the js-controller **v2.1.1** as of 27.11.2019.

It is a ** minimal installation ** containing only the admin, info and discovery adapters **.
Further adapters and their instances still have to be created and configured.

Creating additional adapters and their instances is described in [here](/tutorial/adapter.md).

** Note! ** The following instructions have been made to the best of our knowledge with the information at the time of the creation of the image. Updates to packages or the kernel can change anything at any time.

The image is localized for Germany. If using in other environments please adjust accordingly. (`sudo raspi-config`; 4.) Localization Options)

## After the first start
After the first start of the Rapberry Pi, please make the following settings with `sudo raspi-config`:

* Point 1: `Change User password` (own password for the user` Pi` assigned)

* Point 2: `Network Options - Hostname` (change the name of the Raspberry Pi, default is` raspberrypi`)

If the hostname is changed, please enter `iobroker host this` in the console in the installation directory

* Item 7: `Advanced Options - Expand filesystem` (Extend the root filesystem up to the maximum size of the used SD card)

* if necessary still under point 4: `Localization Options` make adjustments. The default settings apply to Germany

## System Update
As it may have been some time since the image was created at the time of the download, you should first update the system.

To bring Linux and nodejs up to date versions, you can do the following on the console:

```sudo apt-get update && sudo apt-get upgrade -y```

In addition, you should check whether there are already updates to the already installed adapters and the js-controller (see tab Hosts).

In addition to the smallest possible size of an image, this is also the reason that only a few adapters are already pre-installed.

In such cases always first run the js-controller via the console according to the instructions in the tab Hosts, then if necessary the adapter Admin and then all other adapters.

## Installation of Redis
These images no longer contain the database Redis to save the states. With weak computers and low RAM, the use of Redis increases the performance in some cases considerably. With faster computers, it reduces the write access and thus prolongs the life of the SD card.

If you want to install Redis you have to proceed with the current images as follows.

### Installing the Redis server
After the command:

`sudo apt install redis-server`

If the Redis server is ready, it is available on port 6379

### Switching States to Redis
The use of Redis to store the states in ioBroker must be configured in the console with:

`iobroker setup custom`

In the dialog that follows, enter the following (Attention in the 4th line):

```
Type of objects DB [file, couch, redis], default [file]: ENTER
Host of objects DB(file), default[127.0.0.1]: ENTER
Port of objects DB(file), default[9001]: ENTER
Type of states DB [file, redis], default [file]: r ENTER
Host of states DB (file), default[HostName]:ENTER
Port of states DB (file), default[9000]: ENTER
Host name of this machine [hostname]: ENTER
```

Special features when installing in a multi-host system are described here:

[Click here](config/multihost.md)

Release of redis for the user iobroker the backitup adapter can also access redis, the user must be given the necessary rights with:

`sudo usermod -a -G redis iobroker`