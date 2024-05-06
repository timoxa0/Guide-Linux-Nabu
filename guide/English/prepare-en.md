<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">


# Running Linux on the Xiaomi Pad 5

## Preparing your device [→](install-en.md)

### Prerequisites
- Brain

- [Vbmeta image](https://timoxa0.su/share/nabu/manual/vbmeta_disabled.img)

- [Recovery Image](https://timoxa0.su/share/nabu/manual/orangefox.img)

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

#### Reboot tablet to bootloader

#### Flash vbmeta_disabled.img via fastboot
```
fastboot flash vbmeta_ab <vbmeta_disabled.img>
```
> Replace <vbmeta_disabled.img> with path to vbmeta_disabled.img

#### Boot Orange Fox recovery through PC
```
fastboot boot <recovery.img>
```
> Replace <recovery.img> with path to recovery.img

#### Repartition yout device
```
adb shell partition [TARGET LINUX SIZE IN GB]
```

#### Create dtbo backup
```
adb shell backupdtbo
adb pull /tmp/dtbo.img
```
> Backup will be saved to current directory

#### Check if Android still starts
Just restart the tablet, and see if Android still works. If isn't boot or looping or animation, wipe data in recovery.

### [Next step: Installing Linux](/guide/English/install-en.md)
