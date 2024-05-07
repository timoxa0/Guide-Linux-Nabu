<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">

# Running Linux on the Xiaomi Pad 5

## [←](./prepare-en.md) Installing Linux

### Prerequisites
- Brain
  
- [Rootfs image](https://timoxa0.su/?dir=share/nabu/images/v2)

### Notes:
> [!Warning]\
> All your data will be erased! Backup now if needed.

### Installation

1. #### Download and extract rootfs image

2. #### Reboot device to bootloader

3. #### Flash image to device using deployer
```
lon-deployer /path/to/rootfs.img
```
Deployer will ask you for username, password and linux partition size

> After the final reboot, a menu will appear that you can navigate using the volume and power buttons

### Done!
