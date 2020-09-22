# D-Link firmwares

D-Link firmwares can be downloaded at the follwoing addresses:
- ftp://ftp2.dlink.com/PRODUCTS/
- http://files.dlink.com.au/Products/

Some sources are available at the following address:
- https://tsd.dlink.com.tw/downloads2008list.asp?OS=GPL

## Decompression
A few decompression tests have been done, some being more successful than others:

### dir635_firmware_104.bin
This firmware coud not be extracted. Here's the header: `fa 32 00 80 01 04 00 03`. Strings only reveals partial piece of
strings. Here's the entropy analysis from binwalk:
TODO image

### DIR635B3_FW234EUB07.bin
This firmware could be partially extracted. Binwalk finds an arj file at `0x46F4` which contains a single file: `img.bin`.
From this file, binwalk can extract known files but no directory structure could be found. For this `img.bin` file, here 's
the header: `fa 32 00 80 07 00 04 01`. Here's the entropy analysis from binwalk:
TODO image

### DIR657A1_FW100B07.bin
From this firmware, the cpio-root filesystem can be extracted only with binwalk
