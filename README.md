# Notes
Turn off hardware flow control in minicom or you won't be able to send keys

## System information:
```
CPU:   Broadcom BCM63168D0
DRAM:  256 MiB
NAND:  128 MiB
Board Id (0-6)                    : F@ST3865b

Total Memory: 268435456 bytes (256MB)
Boot Address: 0xb8000000

NextLevelBoot U-boot @ 0x8ff00000
Chip ID: BCM63168D0, MIPS: 400MHz, DDR: 400MHz, Bus: 200MHz

NAND Config: Reg=15142200, chipSize=128 MB, blockSize=128K, erase_shift=11
busWidth=1, pageSize=2048B, page_shift=11, page_mask=000007ff
```

## Dumping the flash:
```
./cfetool.py --read=test.bin --addr=0xb8000000 --size=0x8000000 --block=0x20000
```

## Future Work
Find an image from a router with the same CPU and try to boot it.
Some other page mentions that the BBOX3 is simply a rebrand of a Sagemcom F@ST 3864.
Browsing the [OpenWRT builds](https://downloads.openwrt.org/) leads me to brcm63xx
and consequently to the [FAST2704V2-squashfs-cfe.bin](https://downloads.openwrt.org/releases/17.01.4/targets/brcm63xx/generic/lede-17.01.4-brcm63xx-generic-FAST2704V2-squashfs-cfe.bin). I will
attempt to boot this via tftpboot. The assumption is that it is from a similar brand
and seeing as tftpboot should boot from RAM and not flash, hopefully the device will
not be bricked
