﻿


# Matebook-D15-2020-OpenCore Hackintosh

```
 This project supports the Intel version of the Huawei Matebook D15 (2020)
```

|  | |
|:--------------:|:------------------------------------------------------------------------------------------------------------------:|
|Model | Huawei Matebook D15 **2020**|
| CPU |    Intel Core i5 10210U / i7 10510U (Comet Lake) |
| GPU | Intel UHD620 </br> Nvidia MX250 / MX350 |
|RAM  |     8GB / 16GB LPDDR3|
| WiFi/BT  | Intel 9560AC CNVio <br>|
| Trackpad|  ETD2204  |
| Audio |  ALC256 |
|Storage | ~~SAMSUNG PM981 (not supported)~~ <br> WDC PC SN730 </br>|
| Display | 1920*1080|
|SMBIOS | MacBookPro 16,3|
| BIOS | Latest version|
--------
  

## Changelog:

  

<details>

<summary>click for details</summary>

  

- 24/04/22

Inital release (0.7.9)

</details>

  

## Compatible：

1. Bluetooth

2. WIFI

3. Sleep-Wakeup
  
4. HDMI

5. TrackPad

7. Perfect power management (disable CFG Lock first)

8. iGPU (UHD630)

9. CPU Boost

10. USB Mapping

11. FN hot key (brightness and sound)

12. Audio (headphone jack/speakers)


  

## Incompatible

1. Webcam
（UVC Camera VendorID_1480 ProductID_975 is available）
	*_Use a USB webcam as a workaround_

2. Dedicated Nvidia MX250 GPU

3. DRM enabled video content in Safari, Apple TV, and the Music app.
	(for online streaming, use Google Chrome. Apple Music is sometimes unable to play Dolby Atmos and other Lossless content however local files work fine. DRM can't be fixed as it requires a dedicated AMD GPU.)
	
## About installation

  

<details>

<summary>⚠️Preprocessing：inject SSN,UUID,ROM,MLB (click for details)</summary>

Make sure to configure your PlatformInfo before booting.

Read [Dortania's Install Guide](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/coffee-lake-plus.html#platforminfo) for more info.

Use [ProperTree](https://github.com/corpnewt/ProperTree) to edit the config.plist.

</details>

  

<details>

<summary> How to install：</summary>


Check out [Dortania's Install Guide](https://dortania.github.io/OpenCore-Install-Guide/) for more info. 

This is a Comet Lake Intel laptop.
  
</details>

## Important notes

  

<details>

<summary>⚠️Warning</summary>

⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️

1. Do not attempt to boot Windows via OpenCore.

The ACPI files attempt to inject themselves into Windows, preventing it from booting. So you won't be getting far anyway.

You should just set macOS as the default boot option via OpenCore by pressing **Ctrl + Enter** to choose Mac partition while on the boot picker.

and edit config.plist to disable "showpicker" which is at EFI/OC.

then press F12 immediately after you press power button, and choose the option called "Windows Boot Manager" to boot Windows with original UEFI bootloader.


2.You should edit the config.plist to customize MLB/SN/UUID which is unique before you start to use your laptop as daily pc.


</details>

  

  

  

<details>

<summary>Install ComboJack to fix audio jack  </summary>

![image](https://github.com/ske1996/matebook-13-2019-oc-efi/blob/master/%E6%9D%82%E9%A1%B9/audiojack.png?raw=true)

  

  

From Heporis:

  

https://github.com/randomprofilename/ComboJack

  

  

run install.sh in terminal:
(You may need to enable the ROOT user under macOS Monterey for this to work.)

  

```bash

ComboJack_Installer/install.sh

```

</details>

  

  

  

  

  

<details>

<summary>How to disable CFG lock：(required to boot) </summary>

  

✨For perfect power management and smooth boost

if you got unnormal cpu boost issue or overheating issue,i recommand to do this

  

  

  

1.Format a usb stick to fat32

  

2.create a new floder named "EFI" at root

  

3.create a new floder named "BOOT" At /EFI

  

4.download [cfgunlock.zip(click)](https://github.com/ske1996/matebook-13-2019-oc-efi/raw/master/cfgunlock.zip)

  

5.copy bootx64.efi from cfgunlock.zip to EFI/BOOT in your usb

  

Restart and boot with this usb

  

After you boot

  

Press alt and "＝" in same time

(BTW,my keyborad is standard USA version,the hot key is not same between different language version keyboard,so strongly recommand to get an external USA version keyborad for this guide)

  

And use ↑and↓ in your keyboard to find "cpusetup"

  

  

And press enter in keyboard to enter "cpusetup"

  

  

You will see this.

![image](https://github.com/ske1996/matebook-13-2019-oc-efi/blob/master/%E6%9D%82%E9%A1%B9/RU.jpg?raw=true)

  

0030-0E in your computer must be 01

  

Use ←→↑↓ key to pick it and press enter

  

Then,put "00" in

  

Then,press ctrl and w in same time to save setting

  

If save successfully,it will tell you like"update written"(i forget what it was)

  

And alt+q to quit

  

Btw, DO NOT use opencore to boot what i uploaded

  

You should use that usb stick to boot again for check the change is saved

then use [propertree](https://github.com/ske1996/matebook-13-2019-oc-efi/raw/master/ProperTree.zip) to change kernel/add/quirks which is at EFI/OC/config.plist of ESP partition as this picture

![image](https://github.com/ske1996/matebook-13-2019-oc-efi/blob/master/%E6%9D%82%E9%A1%B9/cfgunlosk.png?raw=true)

  

That is all of how to unlock cfg for matebook D series laptop.

  

And you will get a perfect power management

  

</details>

<details>

<summary>Change DMVT to 64 MB (also required to boot) </summary>

(you'll need an external keyboard for this one as we don't have the Page Down key)

our dvmt is 32mb in defult,and it just support hdmi output to 4k30p

  

and you can get 4k60p hdmi output work after you unlock dvmt to 64mb

  

basically same as my cfg guide

  

use that bootx64.efi from cfgunlock.zip,copy it to EFI/BOOT in your usb stick and boot with it

  

after you boot with that usb stick,press alt and = at same time in usa version keyboard

  

use "pagedown" to find SaSetup and get into it

  

then press crtl and pgdown ,your screen will like that picture

![image](https://github.com/ske1996/matebook-13-2019-oc-efi/raw/master/%E6%9D%82%E9%A1%B9/dvmt64.bmp)

  

change 0107 to 2 and 0108 to 3

  

then crtl and w to save the change

  

You should use that usb stick to boot again for check the change is saved

At last,dont forget to remove these three properties which are named “framebuffer-fbmem” “framebuffer-stolenmem” “framebuffer-unifiedmem” in framebuffer part of config.plist with [propertree](https://github.com/ske1996/matebook-13-2019-oc-efi/raw/master/ProperTree.zip).

  

[the inspiration of this guide from @laozhiang](https://github.com/laozhiang)

  

  

</details>

  

<details>

<summary>fix time issue between windows and macos(for double boot)</summary>

in windows press WIN+x run CMD with administrator

input：

```bash

Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_DWORD /d 1

```

  

  

</details>

  

## Credits
  

- [@intel](https://www.intel.com/content/www/us/en/homepage.html) produce cpu for us

  

- [@apple](https://www.apple.com/) created macos

- [@zxystd](https://github.com/OpenIntelWireless/itlwm) created kexts of wifi and bluetooth

  

- [@ske1996](https://github.com/ske1996/Matebook-D14-2020-hackintosh) For the original ACPI files and config.plist.
