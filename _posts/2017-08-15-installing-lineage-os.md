---
layout: post
title: "Installing Lineage OS"
category: posts
---

Stock Android is great. It runs seemlessly and is unbloated. And that's why manufacturers who ship device with Stock Android release updates quickly. For couple of years, I have been using using stock android on day-to-day basis. Therefore, I decided to switch to custom android for a change.

So, what are the options available? <br/>
There is Lineage OS (previously Cyanogen), Paranoid Android, MIUI to list a few. Having seen Cyanogen on my friend's phone, I also have been meaning to try Lineage OS on my phone for a while. So, I decided to give Lineage OS a shot. Installation is pretty straight forward these days. I am assuming platform tools like `adb` and `fastboot` are installed on your system.

{% include important.html content="Performing below steps will void your warranty. Please proceed accordingly." %}

## Unlocking Bootloader

I have Moto G4 Plus (athene), henceforth I have to register on [Motorola's website](https://motorola-global-portal.custhelp.com/app/standalone/bootloader/unlock-your-device-a) for unlocking the bootloader. Here are [steps](https://motorola-global-portal.custhelp.com/app/standalone/bootloader/unlock-your-device-b) listed in brief:

* Connect your device to your system and boot the device to Bootloader mode.
	
```
	adb reboot bootloader
```

* Check if your device is listed in terminal.
	
```
	fastboot devices
```

* Get unlock data.
	
```
	fastboot oem get_unlock_data
```

* A string will be returned which will be used to get unlock key. It will look like this:

```
On a Windows Desktop, the returned string format would be
	(bootloader) 0A40040192024205#4C4D3556313230
	(bootloader) 30373731363031303332323239#BD00
	(bootloader) 8A672BA4746C2CE02328A2AC0C39F95
	(bootloader) 1A3E5#1F53280002000000000000000
	(bootloader) 0000000

On a Mac OS Desktop, the returned string format would be 
	INFO0A40040192024205#4C4D3556313230
	INFO30373731363031303332323239#BD00
	INFO8A672BA4746C2CE02328A2AC0C39F95
	INFO1A3E5#1F53280002000000000000000
	INFO0000000
```
	
* Paste together the 5 lines of output into one continuous string without (bootloader) or ‘INFO’ or white spaces. Your string needs to look like  this:
	
```
0A40040192024205#4C4D355631323030373731363031303332323239#BD008A672BA4746C2CE02328A2AC0C39F951A3E5#1F532800020000000000000000000000
```

* Check your string at [Moto's website](https://motorola-global-portal.custhelp.com/app/standalone/bootloader/unlock-your-device-b). If your device is unlockable, you will get unlock key.

* Unlock your bootloader.
	
```
	fastboot oem unlock "KEY"
```

* Congratulations, your device is now unlocked. :)

## Installing Custom Recovery

There are a bunch of options for custom recovery too. I decided to use TWRP due to its popularity. Here are steps to install TWRP:

* Download latest TWRP from [here](https://twrp.me/Devices/).

* Install TWRP.
	
```
	fastboot flash recovery twrp-3.1.1-0.img
```

* Remember you should get 'OKAY' after executing each command.

## Flashing Lineage

I followed guide listed on Lineage OS for flashing the ROM. It is a great guide and covers various problems you may run into. You can find guide [here](https://wiki.lineageos.org/devices/athene/install).

## Final Notes

Huge thanks to [XDA Community for Moto G4 Plus](https://forum.xda-developers.com/moto-g4-plus) and [Lineage OS Wiki](https://wiki.lineageos.org/devices/athene/install). I have succesfully installed Lineage on my phone and probably use for couple of days. 

{% include tip.html content="Please go through XDA and Lineage OS Wiki atleast once before proceeding. You may unearth some minute details which may prevent your device from bricking. I am and will not liable for your bricked device." %}