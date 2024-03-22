<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">

# Running Linux on the Xiaomi Pad 5

## [←](prepare-en.md) Installing Linux

### Prerequisites
- Brain
  
- Rooted Android
  
- [Rootfs image](./distros-en.md)

- [Kernel image](https://timoxa0.su/share/nabu/images/linux-6.1.10-nabu-gc033672c6f54.boot.img)

- [UEFI installer](https://timoxa0.su/share/nabu/uefi-installer-nabu.zip)

### Installation

#### Reboot to fastboot to install Linux

#### Flash Linux image via fastboot
```
fastboot flash linux <rootfs.img>
```
> Replace <rootfs.img> with path to rootfs image

#### Reboot to bootloader
```
fastboot reboot bootloader
```

#### Erase dtbo
```
fastboot erase dtbo
```

#### Temporary boot Linux from PC
```
fastboot boot <linux-boot.img>
```
> Replace <linux-boot.img> with path to kernel image
> Do dot disconnect tablet from pc until it boots to initial setup

#### Complete initial setup and reboot the tablet into bootloader

#### Restore dtbo backup
```
fastboot flash dtbo <dtbo.img>
```
> Replace <dtbo.img> with path to dtbo backup

#### Reboot tablet into android
```sh
fastboot reboot
```

### Set up dualboot

#### Flash UEFI installer via Magisk or recovery
> After rebooting, a menu will appear in which you can navigate using the volume and power buttons

### Готово!
