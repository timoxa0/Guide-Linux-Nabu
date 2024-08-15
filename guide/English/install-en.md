<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">

# Running Linux on the Xiaomi Pad 5

## [←](./prepare-en.md) Installing Linux

### Prerequisites
- Brain
  
- [Rootfs image](https://timoxa0.su/?dir=share/nabu/images/v3)

### Notes:
> [!Warning]\
> All your data will be erased! Backup now if needed.

> [!Note]\
> If you want to use switch2linux to dualboot add -Q flag to lon-tool command\
> After installation follow this [guide](./linuxswitch-en.md)

### Installation

1. #### Download image

2. #### Reboot device to bootloader

3. #### Flash image to device using deployer
```
lon-tool deploy /path/to/image.lni
```
Deployer will ask you for username, password and linux partition size

> After the final reboot, a menu will appear that you can navigate using the volume and power buttons

### Done!
