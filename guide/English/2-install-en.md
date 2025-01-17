<img align="right" src="https://github.com/woacepheus/Port-Windows-11-Xiaomi-Mi-9/blob/main/cepheus.png" width="425" alt="Windows 11 Running On A Xiaomi Mi 9">


# Running Windows on the Xiaomi Mi 9

## Installation

## Installing Windows

### Prerequisites
- [Windows on ARM image](https://worproject.com/esd)
- [UEFI image](https://github.com/qaz6750/XiaoMi9-Drivers/releases)
- [Drivers](https://github.com/woacepheus/XiaoMi9-Drivers)
- [Modded recovery image](https://github.com/woacepheus/Port-Windows-11-Xiaomi-Mi-9/releases/download/1.0/recovery-cepheus.img) (Should already be installed)

### Boot the modded recovery
> If rebooting on the last page has replaced your recovery back to stock, flash it again in fastboot with:
```cmd
fastboot flash recovery path\to\recovery.img reboot recovery
```

#### Execute the msc script
> If it asks you to run it once again, do so
```cmd
adb shell msc
```

### Assign letters to disks
  
#### Start the Windows disk manager
> Once the Xiaomi Mi 9 is detected as a disk
```cmd
diskpart
```

#### Assign `X` to Windows volume

#### Select the Windows volume of the phone
> Use `list volume` to find it, it's the one named "WINCEPHEUS"

```diskpart
select volume <number>
```

#### Assign the letter X
```diskpart
assign letter x
```

### Assign `Y` to ESP volume

#### Select the esp volume of the phone
> Use `list volume` to find it, it's the one named "ESPCEPHEUS"

```diskpart
select volume <number>
```

#### Assign the letter Y
```diskpart
assign letter y
```

#### Exit diskpart
```diskpart
exit
```

### Installing Windows
> Replace `path\to\install.esd` with the actual path to install.esd.

> If you are using an ISO file, the image file is located in the sources folder inside the ISO. Mount the ISO with Windows Explorer and then copy the path to it.

> Replace `index:6` with `index:1` if your image is not from the link in this guide.

```cmd
dism /apply-image /ImageFile:path\to\install.esd /index:6 /ApplyDir:X:\
```

### Create Windows bootloader files for the EFI
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

### Installing drivers
> You can download Drivers [here](https://github.com/woacepheus/XiaoMi9-Drivers)

> When you downloaded the drivers, go to the tools folder

```cmd
 DriverUpdater.exe -d "<path to extracted drivers>\definitions\Desktop\ARM64\Internal\cepheus.txt" -r "<path to extracted drivers>" -p X:\
```

## Backing up boot images

##### Reboot your recovery
> To remove the msc script
- Reboot to recovery through the modded recovery, or run
```cmd
adb reboot recovery
```

##### Back up your Android boot image
> Use the TWRP backup feature to backup your Android boot image. Name this backup "Android"

##### Push the UEFI to your phone
> Drag and drop MuCepheusSecureBoot.img to your phone's internal storage.

##### Flash the UEFI
> Use the TWRP install feature to flash the UEFI image to your boot partition. Select "install image", then locate the image.

##### Back up your Windows boot image
> Use the TWRP backup feature to backup your Windows boot image. Name this backup "Windows"

## Boot into Windows
> After having flashed the UEFI image, reboot your phone.

* Your device will now set up Windows. This will take some time. It will eventually reboot, and after that the initial setup (oobe) should launch.
  

### Remove phantom drive letters (if they are not removed automatically)
> Run these commands as an admin to remove the letters
```cmd
mountvol x: /d
mountvol y: /d
```

## Finished!

### [Last step: Setup Dualboot](dualboot-en.md)
