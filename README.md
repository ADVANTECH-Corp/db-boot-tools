# Bootloaders for Advantech products

The bootloader binaries are revised from [96Boards](https://builds.96boards.org/releases/dragonboard410c/linaro/rescue/17.04/).

The difference between ours & 96Boards:

**[advantech_bootloader_emmc_android-79]**

- Partition table which supports CDT binary (from aosp-79)
- New CDT binary
- New flash script
- [Revised bootloader (LK)](https://github.com/ADVANTECH-Corp/lk/tree/release/LA.BR.1.2.7-03810-8x16.0) for bootup stability
    - commit *cd13e9c6ff3b65a5e748652423429c2d225140c3*

**[advantech_bootloader_emmc_linux-79]**

- Partition table which supports OTA feature
- New CDT binary
- New flash script
- [Revised bootloader (LK)](https://github.com/ADVANTECH-Corp/lk/tree/release/LA.BR.1.2.7-03810-8x16.0) for bootup stability & fastboot_trigger
    - commit *e61cf232875231585e1e86c9acf797c2cfb7f0ed*
- Default cache image

**[advantech_bootloader_sd_linux-79]**

- New CDT binary
- [Revised bootloader (LK)](https://github.com/ADVANTECH-Corp/lk/tree/release/LA.BR.1.2.7-03810-8x16.0+sdboot) for bootup stability & fastboot_trigger
    - commit *7801629c269badfb0cedb129c98e872c110a2ac1*
- Default cache image

**[advantech_sdcard_rescue-79]**

- [Revised bootloader (LK)](https://github.com/ADVANTECH-Corp/lk/tree/release/LA.BR.1.2.7-03810-8x16.0+rescue) for bootup stability & empty MBR
    - commit *7eaa251dd694a5288e3da879c9bd500a3de8338b*

