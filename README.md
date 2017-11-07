# Bootloaders for Advantech products

The bootloader binaries are revised from [96Boards](https://builds.96boards.org/releases/dragonboard410c/linaro/rescue/17.09/).

The difference between ours & 96Boards:

**[advantech_bootloader_emmc_linux-88]**

- Partition table which supports OTA feature
- New CDT binary
- New flash script
- [Revised bootloader (LK)](https://github.com/ADVANTECH-Corp/lk/tree/release/LA.BR.1.2.7-03810-8x16.0) for bootup stability & fastboot_trigger
    - commit *c6f4a3dd947b5d2fcbc40cf4be32c7ef403a1286*
- Default cache image

**[advantech_bootloader_sd_linux-88]**

- New CDT binary
- [Revised bootloader (LK)](https://github.com/ADVANTECH-Corp/lk/tree/release/LA.BR.1.2.7-03810-8x16.0+sdboot) for bootup stability & fastboot_trigger
    - commit *46968cd9ae22196d559e8d9ffbe6e4c7c4e2744a*
- Default cache image

**[advantech_sdcard_rescue]**

- No change in this version. Please get [advantech_sdcard_rescue-79](https://github.com/ADVANTECH-Corp/db-boot-tools/raw/17.04-adv/advantech_sdcard_rescue-79.zip).

**[advantech_bootloader_emmc_android]**

- No change in this version. Please get [advantech_bootloader_emmc_android-79](https://github.com/ADVANTECH-Corp/db-boot-tools/raw/17.04-adv/advantech_bootloader_emmc_android-79.zip).

