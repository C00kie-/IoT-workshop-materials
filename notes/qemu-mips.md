## Problem Statement

- Firmware are developed to be executed on dedicated hardware
- Emulating a complete embedded hardware (dedicated board, interface) is hard
- Executing binaries is an option to perform dynamic analysis

This note includes the complete steps to extract binaries, setup a qemu VM to run the extracted binaries and perform further analysis on the results.

## Running extracted binaries from a firmware in qemu

### Using qemu

#### Using a default Debian as bootstrap

[https://people.debian.org/~aurel32/qemu/](https://people.debian.org/~aurel32/qemu/) provides a set of qemu images along with the Linux kernel for each architecture.

#### How to select the architecture?

There are various options in order to know the architecture of the firmware. One is to run the `file` command against one of the binary.

~~~~console
adulau@dobbertin:~/git/workshop-materials/extracted-firmwares/Netgear-N300/_mtdblock2.bin.extracted/squashfs-root/bin$ file busybox
busybox: ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), dynamically linked, interpreter /lib/ld-, corrupted section header size
~~~~


