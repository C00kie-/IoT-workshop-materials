## Problem Statement

- Firmware are developed to be executed on dedicated hardware
- Emulating a complete embedded hardware (dedicated board, interface) is hard
- Executing binaries is an option to perform dynamic analysis

This note includes the complete steps to extract binaries, setup a qemu VM to run the extracted binaries and perform further dynamic analysis.

## Configuration hints during the workshop

- SSH port is 5555

## Running extracted binaries from a firmware in qemu

### qemu

#### Default Debian as bootstrap

[https://people.debian.org/~aurel32/qemu/](https://people.debian.org/~aurel32/qemu/) provides a set of qemu images along with the Linux kernel for each architecture.


#### How to select the architecture?

There are various options in order to know the architecture of the firmware. One is to run the `file` command against one of the binary.

~~~~console
adulau@dobbertin:~/git/workshop-materials/extracted-firmwares/Netgear-N300/_mtdblock2.bin.extracted/squashfs-root/bin$ file busybox
busybox: ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), dynamically linked, interpreter /lib/ld-, corrupted section header size
~~~~

#### starting qemu

~~~~console
qemu-system-mips -M malta -kernel vmlinux-3.2.0-4-4kc-malta -hda debian_wheezy_mips_standard.qcow2 -append "root=/dev/sda1 console=tty0" -device e1000-82545em,netdev=user.0 -netdev user,id=user.0,hostfwd=tcp::5555-:22
~~~~

- In the command above, we select a default Debian MIPS image (as mentioned above).
- We add an ethernet device (with a driver supported by MIPS architecture).
- A `hostfw` rule (redir is not used anymore in recent version) is to redirect the SSH port (TCP/22) on the local TCP/5555.

#### Copying firmware filesystem to qemu

~~~~console
adulau@dobbertin:~/git/workshop-materials/extracted-firmwares/Netgear-N300/_mtdblock2.bin.extracted$ scp -P5555 sq.tar.gz root@127.0.0.1:/root 
root@127.0.0.1's password: 
sq.tar.gz                                                                                                                                                   100% 3517KB   3.2MB/s   00:01
~~~~

#### Extracting squashfs

~~~~console
root@debian-mips:~# tar xvfz sq.tar.gz
~~~~

#### chroot to the squashfs

~~~~
cd squashfs-root
root@debian-mips:~# chroot . ./bin/sh
mount -t proc proc proc/
mount --rbind /sys sys/
mount --rbind /dev dev/
~~~~


