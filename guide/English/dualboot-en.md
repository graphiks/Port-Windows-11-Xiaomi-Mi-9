<img align="right" src="https://github.com/woacepheus/Port-Windows-11-Xiaomi-Mi-9/blob/main/cepheus.png" width="425" alt="Windows 11 Running On A Xiaomi Mi 9">


# Running Windows on the Xiaomi Mi 9

## Dualbooting Android and Windows seamlessly

### Prerequisites
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
- [Modified TWRP](https://github.com/woacepheus/Port-Windows-11-Xiaomi-Mi-9/releases)
- [NTFS Android Magisk Module](https://github.com/woa-vayu/Port-Windows-11-POCO-X3-Pro/releases/ntfsdroid)
- [UEFI](https://github.com/qaz6750/XiaoMi9-Drivers/releases)
- [Windows on Android Helper APK (test version)](https://t.me/WinOnMi9/328)
- [StA Installer](https://github.com/woa-vayu/Port-Windows-11-POCO-X3-Pro/releases/dualboot)

### Phone Setup

#### Adding NTFS Support to android
- Install Magisk if you haven't already
- Install the NTFS Android magisk module through the Magisk manager

#### Application Setup
> [!NOTE]
>
> In order to mount Windows while you're booted in Android, you need to "shut down" Windows properly. To do this, restart Windows and then boot into TWRP as the screen fades to black. From here you can switch back to Android using the backup you made earlier.
- Download the StA Installer and the Windows on Android Helper APK, then install the APK
- Create a folder named "UEFI" on your internal storage
- Copy the uefi image into the UEFI folder
- Open the app and allow any root access it wants
- Press the "BACKUP ANDROID BOOT" button, then dismiss the popup
- Press the "Mount/Unmount Windows button, then dismiss the popup
- Go to your file explorer and Windows should be mounted in sdcard/Windows (your internal storage). Move the StA Installer and boot.img backup into this folder
- Return to the WOA helper app and press "Quickboot to Windows"
- After Windows boots, run the StA installer in the C:\ directory
> You may need to disable any antivirus software present, if the installer does not work

#### Booting to Android
  
  - Run the new shortcut on your desktop as **ADMINISTRATOR**

#### Booting to Windows
  
  - Run the app
  - Press "Quickboot to Windows"

> If quickboot does not work, you may have shut down Windows incorrectly. If this happens, use the "Flash UEFI" button and manually reboot your phone.
  
## Finished!
