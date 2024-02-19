<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">


# Running Linux on the Xiaomi Pad 5

## Preparing your device [→](install-en.md)

### Prerequisites
- Brain

- [Vbmeta image](https://github.com/timoxa0/Guide-Linux-Nabu/releases/download/v0.0.1/vbmeta_disabled.img)

- [Recovery Image](https://github.com/timoxa0/Guide-Linux-Nabu/releases/download/v0.0.1/orangefox.img)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

### Notes:
> [!Warning]\
> All your data will be erased! Backup now if needed.
> 
> These commands have been tested.
> 
> Ignore `udevadm` warnings
> 
> Do not run the same command twice
>
> Do not run all commands at once, execute them in order!

#### Flash vbmeta_disabled.img via fastboot
```sh
fastboot flash vbmeta_ab <vbmeta_disabled.img>
```
> Replace <vbmeta_disabled.img> with path to vbmeta_disabled.img

#### Boot Orange Fox recovery through PC
```sh
fastboot boot <recovery.img>
```
> Replace <recovery.img> with path to recovery.img

#### Start ADB shell
```sh
adb shell
```

#### Unmount all partitions
```sh
twrp unmount /data
```

#### Resize partition table
```sh
sgdisk --resize-table 64 /dev/block/sda
```

#### Run parted partition editor
```sh
parted /dev/block/sda
```

#### List partitions with `print` and remember userdata number

```
...
31      10.9GB  126GB   126GB                userdata
...
```
> In this cae  userdata has number 31

#### Remove userdata with `rm <номер>`
> If userdata has number 31, command looks like `rm 31`

#### Create userdata partition
- Calculate userdata size using equation: X = 10.9 + [userdata size in GB]
- Run command `mkpart userdata ext4 10.9GB XGB` (replace X with calculated vaule)
> If userdata size is 16 GB, then X = 10.9 + 16 = 26.9 \
> So command is `mkpart userdata ext4 10.9GB 26.9GB`

#### Create efi partition
```
mkpart esp fat32 XGB YGB
```
> Replace X with value calculated in prevous paragraph \
> Replace Y with X+1 \
> If userdata size is 16 GB, then command is `mkpart esp fat32 26.9GB 27.9GB`

#### Create partition for linux
- for 128 GB model: `mkpart linux ext4 YGB 126GB`
- for 256 GB model: `mkpart linux ext4 YGB 254GB`
> Replace Y with X+1 \
> If userdata size is 16 GB, then command is \
> `mkpart linux ext4 27.9GB 126GB` for 128 GB model \
> `mkpart linux ext4 27.9GB 254GB` for 256 GB model

#### Quit from parted
```
quit
```

#### Format created ESP patition
```
mkfs.fat -F32 -s1 /dev/block/platform/soc/1d84000.ufshc/by-name/esp -n ESPNABU
```

#### Exit from adb shell
```
exit
```

#### Create dtbo backup
```
adb shell "dd if=/dev/block/platform/soc/1d84000.ufshc/by-name/dtbo$(getprop ro.boot.slot_suffix) of=/tmp/normal_dtbo.img"; adb pull /tmp/normal_dtbo.img
```
> Backup will be saved to current directory

#### Check if Android still starts
Just restart the tablet, and see if Android still works. If isn't boot or looping or animation, wipe data in recovery.

### [Next step: Installing Linux](/guide/English/install-en.md)
