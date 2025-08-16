tarmac.mitel_omm
=========

This role installs the `Mitel Open Mobility Manager (OMM)` onto a Rocky Linux (9) machine.
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

This role only installs OMM Version `9.2-JF12` onto a Rocky `9`.
All other versions will not work.

Access to the Mitel Software is only granted to customers / dealers.
After downloading it copy the following binaries into a folder called `binaries` (which resides in the same root as the calling playbook):
```
$ sha256sum binaries/*
9b31e1deea05e087ca1a740d5e977e4ce21be384e6d1c653f898e313156ad5ce  binaries/iprfp3G.dnld
0982470f09a23552b235f8fd4c146964118b16515418d1ff2a5a9738e378d390  binaries/iprfp4G.dnld
24685dae7d09fad72d97fd19876103810e35de53765a618320de0c0a60b25e8a  binaries/SIP-DECT-HANDSET-9.2__JF12-0.i686.rpm
f45e2c5bbdef222b9716b8d5f4c8bb09d9c1df1b6bd6088a0955f776f27c5bd7  binaries/SIP-DECT-OMM-9.2__JF12-0.i686.rpm
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
