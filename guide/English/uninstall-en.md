<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">

# Running Linux on the Xiaomi Pad 5

## Uninstallation

### Why is this needed?

If you want to uninstall linux this is used instead of deleting partitions manually to avoid human error + writing a whole dedicated guide to just uninstalling.

If you want to relock your bootloader you'll need your partition table to be stock.

### Prerequisites

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
- [gpt_both0.bin]()

### Restore GPT
> Replace ```<gpt_both0.bin>``` with the path to the gpt_both0.bin file.

```cmd
fastboot flash partition:0 <gpt_both0.bin>
```

### Erase userdata to avoid bootloop and restore FS size
```cmd
fastboot -w
```
