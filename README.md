tarmac.mitel_omm
=========

This role installs the `Mitel Open Mobility Manager (OMM)` onto a Rocky Linux (8) machine.
It also installs a `tftp` server with the fimware files for the `RFPs`.


Introduction
------------

In order to use the `Mitel DECT System` you need a few things:

* DECT phones
* Radio Fixed Parts (aka DECT antennas)
* Controller Software (the `Open Mobility Manager` aka `OMM` )

You can either start the `OMM` on one of the antennas or as application on a RHEL system.
This role assumes that you want to install an `OMM` onto a Rocky Linux.

For further information please check out

* [Setting up a Mitel SIP-DECT RFP for home/enthusiast use](https://howto.dect.network/)
* [EVENTPHONE Wiki](https://eventphone.de/doku/)
* [Das neue Eventphone (PoC) Telefonsystem](https://media.ccc.de/v/eh19-179-das-neue-eventphone-poc-telefonsystem)

Limitations/Quirks
------------------

This role only installs OMM Version `8.3_SP5_IC31` onto a Rocky `8`.
All other versions will not work.

Access to the Mitel Software is only granted to customers / dealers.
After downloading it copy the following binaries into a folder called `binaries` (which resides in the same root as the calling playbook):
```
$ sha256sum binaries/*
ec3b00f3201f2af951d090a9f8a2bc3a7a8482361b01439efaac63c8bccb1bfa  binaries/iprfp3G.dnld
450f6cccc629a42dc0afd5e4a8fe81e33da953832e48936690cacde3974110d4  binaries/iprfp4G.dnld
125bbfa6c02e16a8ac04eb7b12039a02413967bcb6633ac4c32fe617d42deb4d  binaries/SIP-DECT-HANDSET-8.3_SP5_IC31-0.i686.rpm
ad11e1d0022c67b22f3bdebc8854054d8be2d554e6a3ff1a08a18fb4766c9697  binaries/SIP-DECT-OMM-8.3_SP5_IC31-0.i686.rpm
```

**The role asserts the checksum of the files**

**Note**:
* Mitel ships the `.rpm` files in a self extracting `.sh` file (i know right ?!) - use `./SIP-DECT.bin -x` to extract them

Requirements
------------

* mitel binaries (see `Limitations/Quirks` for details)

Role Variables
--------------

/

Dependencies
------------

/

Example Playbook
----------------

    - hosts: servers
      roles:
         - tarmac.mitel_omm

License
-------

MIT

Author Information
------------------

Gregor Michels - TARMAC e.V.
