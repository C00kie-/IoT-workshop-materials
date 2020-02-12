needed softwares to perform firmware extraction and analysis 
see : apt-cache policy [package] for version

Serial communication:
minicom (2.7.1build1)

Extraction:
Static binaries
	netcat (MIPS) -https://github.com/darkerego/mips-binaries
	tftp (x86) - (link to provide)

Analysis:
squashfs-tools (1:4.3-12)
binwalk (compiled from sources + dependancies)
	https://github.com/ReFirmLabs/binwalk
	deps.sh script (explain)
		external utilities
		capstone for dissassemble 
		decryption
		... https://github.com/ReFirmLabs/binwalk/blob/master/INSTALL.md






ad1@ad1:~$ apt-cache policy squashfs-tools
squashfs-tools:
  Installed: 1:4.3-12
  Candidate: 1:4.3-12
  Version table:
 *** 1:4.3-12 500
        500 http://archive.linux.duke.edu/ubuntu disco/main amd64 Packages
        100 /var/lib/dpkg/status
ad1@ad1:~$ apt-cache policy minicom
minicom:
  Installed: 2.7.1-1build1
  Candidate: 2.7.1-1build1
  Version table:
 *** 2.7.1-1build1 500
        500 http://archive.linux.duke.edu/ubuntu disco/universe amd64 Packages
        100 /var/lib/dpkg/status
ad1@ad1:~$ apt-cache policy binwalk
binwalk:
  Installed: (none)
  Candidate: 2.1.2~git20180830+dfsg1-1
  Version table:
     2.1.2~git20180830+dfsg1-1 500
        500 http://archive.linux.duke.edu/ubuntu disco/universe amd64 Packages
        500 http://archive.linux.duke.edu/ubuntu disco/universe i386 Packages


