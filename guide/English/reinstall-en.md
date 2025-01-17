<img align="right" src="https://github.com/woacepheus/Port-Windows-11-Xiaomi-Mi-9/blob/main/cepheus.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">


# Running Windows on the Xiaomi Mi 9

## Reinstallation

### Reinstalling Windows if something goes wrong

- If you don't like your windows version or you've bricked your windows install, or anything else, you would probably just reinstall Windows. Thankfully this process is very easy.

- If you haven't restored your partition table, you can use this guide with your existing partitions.

### Prerequisites

- Existing Windows and boot partitions (*If not met, [go back and just pretend this guide never existed](/guide/English/1-partition-en.md)*)

- [Recovery Image](../../../../releases/tag/1.1)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [UEFI (for msc)](https://github.com/woacepheus/Port-Windows-11-Xiaomi-Mi-9/releases/download/1.1/samsung.img)

### Boot recovery to format the Windows and boot partitions

```cmd
fastboot boot <recovery.img>
```
### Format the partitions

```cmd
adb shell format
```

#### Enter to mass storage mode
1. Flash and boot UEFI
2. Select
   `Enter Simple init`
3. Select Mass storage

### Assign letters to disks.. again
  

#### Start the Windows disk manager

> Once the Xiaomi Mi 9 is detected as a disk

```cmd
diskpart
```

- The "WINCEPHEUS" partition should already show up with the letter X. If so, skip to `Assign "Y" to ESP volume`

#### Assign `X` to Windows volume

#### Select the Windows volume of the phone
> Use `list volume` to find it, it's the one named "WINCEPHEUS"

```diskpart
select volume <number>
```

#### Assign the letter X
```diskpart
assign letter=x
```

### Assign `Y` to ESP volume

#### Select the esp volume of the phone
> Use `list volume` to find it, it's the one named "ESPCEPHEUS"

```diskpart
select volume <number>
```

#### Assign the letter Y

```diskpart
assign letter=y
```

- If you get an error saying `The specified drive letter is not free to be assigned`, just restart your computer and try again from diskpart. Do not touch your phone yet.

#### Exit diskpart
```diskpart
exit
```


### Install

- Continue the guide from [here](/guide/English/2-install-en.md#install)
