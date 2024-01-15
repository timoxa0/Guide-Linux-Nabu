<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">


# Running Linux on the Xiaomi Pad 5

## [←](install-en.md) Dualbooting Android and Linux seamlessly

### Prerequisites

- Brain

- Rooted Android

- [boot-loader.tar.xz](https://mega.nz/folder/CVMGEAiB#7oazR3wpkKdAH2eZChtRTg) (Ubuntu-V0.91 recommended)

### Android side of Dual Boot

1) Install [`linuxswitch.apk`](https://github.com/timoxa0/Switch2Linux-Nabu/releases/download/v1.0.2/linuxswitch.apk) to device.
2) Open installed app and grant root access
3) Tap "Dump android images"
4) Move `android.boot.img` and `andoid.dtbo.img` to PC from `/sdcard/linux/`
5) Rename linux boot to `linux.boot.img` and put it to `/sdcard/linux/`
6) Now you can tap "Switch to Linux" to boot linux


### Linux side of Dual boot

1) Download [`s2a.zip`](https://github.com/timoxa0/Switch2Linux-Nabu/releases/download/v1.0.1/s2a.zip)
2) Unzip `s2a.zip` in linux
3) Put `android.boot.img` and `andoid.dtbo.img` into `s2a` folder
4) Install with command
    ```console
    sudo ./install.sh
    ```
5) Now you can reboot to android with Switch2Android app

## Finished!