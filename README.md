# Bootloaders for Dragonboard 410c

The bootloader binaries are copied from 96Boards.
For details, you can refer to
https://builds.96boards.org/releases/dragonboard410c/linaro/rescue/16.09/

- **sdcard_rescue** : an SD card image that can be used to boot from SD card, and rescue a board when the onboard eMMC is empty or corrupted
- **bootloader_emmc_linux** : includes the bootloaders and partition table (GPT) used when booting Linux images from onboard eMMC
- **bootloader_emmc_android** : includes the bootloaders and partition table (GPT) used when booting Android images from onboard eMMC
- **bootloader_sd_linux** : includes the bootloaders and partition table (GPT) used when booting Linux images from SD card
