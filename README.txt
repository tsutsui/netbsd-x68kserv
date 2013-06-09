x68kserv - NFS Server Kit for NetBSD/x68k client


1. What's x68kserv

This "x68kserv" image provides easy setup for X680x0 machines
without supported SCSI I/F to boot NetBSD/x68k using
"root file system on NFS" environment.


2. What x68kserv image contains

This image contains a bootable NetBSD/i386 file system image that
automatically starts daemons like dhcpd(8), mountd(8), and nfsd(8),
and it also contains an NFS exported NetBSD/x68k file system
which has all release binaries including X server and clients.

Since NetBSD 6.1 version, a bootable x68k floppy image that contains
a brandnew netboot loader is also provided for easy bootstrap.


3. Requirements

- x86 based PC with NIC which can boot from USB devices
- 10BASE-T cross cable (or HUB)
- X680x0 machines and Neptune-X or Nereid Ethernet that can
  write a bootstrap netboot floppy image and also can boot from it
- 5.25" 2HD floppy media


4. How to use x68kserv

1) write image to 2GB (or larger) USB flash memory via
   gunzip(1) and dd(1)
   (or Rawrite32.exe tool for Windows),
    Rawrite32.exe tool can be found here:
    http://www.NetBSD.org/~martin/rawrite32/
2) put it on your x86 PC and boot it (per machine specific procedure)
3) connect X680x0 to the x86 x68kserv PC via 10BASE-T cross cable etc.
   note: x68kserv runs dhcpd(8) with its own address (10.0.0.xxx)
   so don't connect it to your open network.
4) prepare bootable NetBSD/x68k floppy that includes netboot:
   # gzcat x68knetbootfd-20130609.img.gz | dd of=/dev/rfd1c bs=15k
   (gzip.x and rawrite.x binaries for Human68k can also be used)
5) boot NetBSD/x68k from the above netboot floppy
6) type enter on following prompts (dump device, file system, init path)
7) have fun


5. Misc

See togetter for netboot details:
http://togetter.com/li/388921

---
Izumi Tsutsui
