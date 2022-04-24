# Matebook-D15-2020-OpenCore Hackintosh  
```
 This project supports the Intel version of the Huawei Matebook D15 (2020)
```

## Update log:  

<details>  
<summary>click for details</summary>  

- 24/04/22
  Inital release (0.7.9)
   
</details> 

## Works fine：

**click "Bluetooth" and "HDMI" "Audio jack and Speaker" for more information**    

<details>  
<summary>1.Bluetooth</summary>   
  
Thanks[@zxystd](https://github.com/OpenIntelWireless/IntelBluetoothFirmware)  
1. HUAWEI bluetooth mouse doesnt work.   
2. Airpods works,but need pairing.    

A list of workable bluetooth mouse:https://github.com/ske1996/matebook-13-2019-oc-efi/issues/156  


</details>   

2. WIFI  


3. Sleep-Wakeup

4. HDMI  

5. TrackPad  
 

6. Perfect power management(after CFG Lock disabled)  

7. IGPU(UHD620)  

8. CPU Boost  

9. USB Mapping

10. FN hot key(brightness and sound)  
 
<details>  
<summary>11. Audio jack and Speaker</summary>   

layout id in 21.  
  
 
and if yours's sells-area is not China,Audio jack and Speaker maybe wont work,cause of different hardware:https://github.com/ske1996/Matebook-D14-2020-hackintosh/issues/24  


</details>   


  
  
## Doesnt work：  


1. Camera（UVC Camera VendorID_1480 ProductID_975 is available）  
*If you need a workable webcam,buy Logicool c270,I'm using it,pretty good.  


2. MX250/150/350（hopeless）

  


## About installation

<details>  
<summary>⚠️Preprocessing：inject SSN,UUID,ROM,MLB (click for details)</summary>  
There were lots of people who installed MacOS without injecting his "SSN,UUID,ROM,MLB" at frist,and that caused Apple service of his apple id blocked.  
So,I made some changes that if you dont inject your "SSN,UUID,ROM,MLB" at frist,you cant boot your hackintosh or installing-processing.  
Google how to do it by yourself.    
But I provide a config editor:  
  
[ProperTree-windows.zip](https://github.com/ske1996/matebook-13-2019-oc-efi/raw/master/ProperTree-windows.zip)  
[Propertree-macos](https://github.com/ske1996/matebook-13-2019-oc-efi/raw/master/ProperTree.zip)   


  
  
</details>   

<details>  
<summary> How to install：</summary> 

A perfect guide in:  

https://dortania.github.io/vanilla-laptop-guide/preparations/installer-overview.html  



</details>  


<details>  
<summary> How to create dual boot：</summary> 

[click to download the guide](https://github.com/ske1996/matebook-13-2019-oc-efi/raw/master/A%20guide%20for%20dualBoot%20of%20Matebook13%20from%20%40Francisco%20Novoa.pdf)  

Thanks [@Francisco Novoa(from Chile🇨🇱)](https://t.me/hackintosh_matebook13/8557) and this dual-boot guide is written by him   


</details>  



## After installation

<details>  
<summary>⚠️Warning</summary>  
⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️⚠️  
  
1.DO NOT BOOT YOUR WINDOWS OR OTHER OS WITH OpneCore.  
you may lose your Genuine license,except you know how to inject your own correct UUID in config.plist.  
it is not 100% happened issue,but it is still risky.  
you should just set Macos as defaul boot at OpenCore with pressing ctrl + enter to choose Mac partition.  
and edit config to disable "showpicker" which is at EFI/OC.  
then press F12 immediately after you press power button,and choose the option named like "windows xxxx" to boot windows with original uefi bootloader.  
Or follow that guide "how to create dual boot" upper this page.  


2.You should edit the config.plist to customize MLB/SN/UUID which is unique before you start to use your laptop as daily pc.  

3.Do not enable "serch my mac" in setting.  

4.Do not enable "file vault" in setting.  


</details>  



<details>  
<summary>Install ComboJack to fix audio jack  </summary>  
  
![image](https://github.com/ske1996/matebook-13-2019-oc-efi/blob/master/%E6%9D%82%E9%A1%B9/audiojack.png?raw=true)  


From Heporis:  

https://github.com/randomprofilename/ComboJack


run install.sh in terminal:  

```bash
ComboJack_Installer/install.sh
```
  
</details>     




  

<details>  
<summary>How to disable CFG lock：</summary>  

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

Btw.DO NOT use opencore to boot what i uploaded  

You should use that usb stick to boot again for check the change is saved  
then use [propertree](https://github.com/ske1996/matebook-13-2019-oc-efi/raw/master/ProperTree.zip) to change kernel/add/quirks which is at EFI/OC/config.plist of ESP partition as this picture 
![image](https://github.com/ske1996/matebook-13-2019-oc-efi/blob/master/%E6%9D%82%E9%A1%B9/cfgunlosk.png?raw=true)  

That is all of how to unlock cfg for matebook D series laptop.   

And you will get a perfect power management  

</details>     
      
<details>  
<summary>Change dvmt to 64mb</summary>  
    
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

## Thanks：

- [@intel](https://www.intel.com/content/www/us/en/homepage.html) produce cpu for us

- [@apple](https://www.apple.com/) created macos  
 
- [@zxystd](https://github.com/OpenIntelWireless/itlwm) created kexts of wifi and bluetooth  

- [@ske1996](https://github.com/ske1996/Matebook-D14-2020-hackintosh) For the original ACPI files and config.plist.
