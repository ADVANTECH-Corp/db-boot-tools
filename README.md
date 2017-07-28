# Bootloaders for Advantech products

The bootloader binaries are revised from [96Boards](https://builds.96boards.org/releases/dragonboard410c/linaro/rescue/latest/).

The difference between ours & 96Boards:

**[advantech_bootloader_emmc_android-79]**

- Partition table which supports CDT binary (from aosp-79)
- New CDT binary
- New flash script
- [Revised bootloader (LK)](https://github.com/ADVANTECH-Corp/lk/tree/release/LA.BR.1.2.7-03810-8x16.0) for bootup stability (commit *cd13e9c6ff3b65a5e748652423429c2d225140c3*)

**[advantech_bootloader_emmc_linux-79]**

- Partition table which supports OTA feature
- New CDT binary
- New flash script
- [Revised bootloader (LK)](https://github.com/ADVANTECH-Corp/lk/tree/release/LA.BR.1.2.7-03810-8x16.0) for bootup stability (commit *cd13e9c6ff3b65a5e748652423429c2d225140c3*)
- Default cache image

**[advantech_bootloader_sd_linux-79]**

- New CDT binary
- [Revised bootloader (LK)](https://github.com/ADVANTECH-Corp/lk/tree/release/LA.BR.1.2.7-03810-8x16.0+sdboot) for bootup stability (commit *dd897cf35a71626cae9078b3c86cac083288ed42*)
- Default cache image

**[advantech_sdcard_rescue-79]**

- [Revised bootloader (LK)](https://github.com/ADVANTECH-Corp/lk/tree/release/LA.BR.1.2.7-03810-8x16.0+sdboot) for bootup stability & empty MBR (commit *7eaa251dd694a5288e3da879c9bd500a3de8338b*)

## How to generate customzied gpt_both0.bin

You can follow the commands below to get new partition table.

```
$ git clone https://github.com/ADVANTECH-Corp/db-boot-tools.git

# to create an empty image (sd.img) with the partition table from linux.txt
$ sudo ./mksdcard -g -o ota.img -p dragonboard410c/linux/partitions.txt

# create a gpt backup
$ sudo sgdisk -bgpt.bin ota.img

# convert gpt backup into proper 'fastboot' format
$ ./mkgpt -i gpt.bin -o gpt_both0.bin
```

Reference: [96Boards Documentation](https://github.com/96boards/documentation/blob/master/ConsumerEdition/DragonBoard-410c/Guides/GPT.md#create-gpt_both0bin)

## How to generate new CDT binary

Before we starts, you need to get Qualcomm `boot_images` source from [ChipCode](https://chipcode.qti.qualcomm.com).

Then, prepare your own DDR.xml and execute the `cdt_generator.py` script.

```
$ cd boot_images/core/boot/secboot3/scripts
$ python cdt_generator.py jedec_lpddr3_single_channel.xml cdt_array.bin

2017-05-16 17:51:43,173 cdt_generator.py 159 INFO: Filename: 'jedec_lpddr3_single_channel.xml'
[['43445400', '0100', '00000000', '00000000']]
[['43445400', '0100', '00000000', '00000000'], ['030801000000']]
[['43445400', '0100', '00000000', '00000000'], ['030801000000'], ['01000000', '00524444', 'FFFF0000', '02000000', 'B8000000', '00000000', '00000000', '00000000', '05000000', '34080000', 'A4010000', '60AE0A00', '76020000', '40010000', '58980000', '98080000', '4B000000', '4B000000', 'D2000000', '64000000', '96000000', '4B000000', 'B4000000', '02000000', '0F000000', '0A000000', '08000000', '0F000000', '0A000000', '08000000', '20000000', '08000000', '03000000', 'B4000000', 'F4010000', '4B000000', '00000000', '00000000', '05000000', '80841E00', '10270000', '04000000', '100E0000', '84030000', '10270000', '0A000000', '96000000', 'F4010000', '80A20000', '00200000', '19000000', '37000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000', '00000000']]
DistanceInBytesToCDB=22
SizeOfLastCDB=6
DistanceInBytesToCDB=28
SizeOfLastCDB=392

Created 'cdt_array.bin'
Created 'boot_cdt_array.c'
```

You are able to get both CDT binary & boot_cdt_array.c files.
The C file can be used in boot_images to build a SBL with hard-code CDT table.
