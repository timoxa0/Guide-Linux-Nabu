<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">


# Running Linux on the Xiaomi Pad 5

## Installing Linux

### Prerequisites
- Brain
  
- [rootfs.img.xz](https://mega.nz/folder/CVMGEAiB#7oazR3wpkKdAH2eZChtRTg) (Ubuntu-V0.91 recommended)

### Installation

#### Extract `rootfs.img` from `rootfs.img.xz`

#### Reboot to fastboot to start installing linux

#### Flash linux image via fastboot
```cmd
fastboot flash linux <rootfs.img>
```
> Replace <rootfs.img> with path to rootfs.img

#### Reboot to android to setup dualboot
```sh
fastboot reboot
```

## Finished!

### [Last step: Setup Dualboot](dualboot-en.md)
