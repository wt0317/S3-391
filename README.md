Patch Install USB
-------------------
1. Remove /Extra/Extensions/AppleACPIPlatform.kext
1. Copy ./Install/GenericUSBXHCI.kext to /Extra/Extensions/
1. Copy ./Install/AppleIntelFramebufferCapri.kext to /System/Library/Extensions

Multibeast
----------
1. Drivers -> Disk -> 3rd Party SATA
1. Drivers -> Graphics -> Intel Graphics Patch for Mixed Systems
1. Drivers -> Misc -> FakeSMC v6.11.1328
1. Drivers -> Misc -> FakeSMC Plugins
1. Drivers -> Misc -> PS/2 Keyboard/Mouse/Trackpad
1. Drivers -> Misc -> USB 3.0 – Universal
1. Drivers -> System -> Patched AppleIntelCPUPowerManagement
1. Bootloaders -> Chimera v4.0.0
1. Customize -> Boot Options -> Basic Boot Options
1. Customize -> Boot Options -> Kext Dev Mode
1. Customize -> System Definition -> Mac Pro -> Mac Pro 3,1
1. Customize -> Themes -> tonymacx86 Black

SMBIOS
------
1. Open ./Utilities/Chameleon Wizard
1. Use MacBookAir5,2

Custom SSDT
-----------
1. Copy ./Extra/SSDT.aml to /Extra/
1. Add ```<key>DropSSDT</key><string>Yes</string>``` to /Extra/org.chameleon.Boot.plist

Note for actual patch:

1. Reboot with final SMBIOS before proceeding
1. Open ./Utilities/ProBook Installer
1. Select only SSDT option and continue install 

Audio
-----
1. Install VoodooHDA_V286_MAV.pkg
1. Copy ./Audio/AppleIntelSNBGraphicsFB to AppleIntelSNBGraphicsFB.kext/Contents/MacOS/
1. Open Audio MIDI Setup
1. Change format to 8ch-16bit Integer
1. Rebuild kext (wi-fi first)

Note for actual patch:

1. Find ```0102 0400 1007 0000 1007 0000
0503 0000 0200 0000 3000 0000
0205 0000 0004 0000 0700 0000
0304 0000 0004 0000 0900 0000
0406 0000 0004 0000 0900 0000```
1. Replace ```0205 0000 0004 0000 0700 0000```
1. With ```0205 0000 0008 0000 0600 0000```

Wi-Fi
-----
1. Add ```<string>pci168c,2b</string>``` to /System/Library/Extensions/IO80211Family.kext/Contents/PlugIns/Info.plist
1. Rebuild cache with Kext Utility

Bluetooth
---------
1. Install ./Bluetooth/IOath3kfrmwr.kext with Kext Utility

Battery
-------
1. Install ./Battery/ACPIBatteryManager.kext with Kext Utility

Keyboard and Trackpad
---------------------
1. Install ./Touchpad & Keyboard/ApplePS2ElanTouchpad.kext with Kext Utility
1. Copy ./Touchpad & Keyboard/Touchpad/Info.plist to /System/Library/Extensions/ApplePS2ElanTouchpad.kext/Contents/
1. Copy ./Touchpad & Keyboard/Keyboard/Info.plist to /System/Library/Extensions/ApplePS2ElanTouchpad.kext/Contents/PlugIns/ApplePS2Keyboard.kext/Contents/

DSDT
----
1. Copy ./Extra/DSDT.aml to /Extra/

Note for patches applied:

1. Open ./Utilities/MaciASL
1. Go to Preferences -> Sources, add http://raw.github.com/RehabMan/Laptop-DSDT-Patch/master
1. Apply Fix TNOT
1. Apply Brightness Fix
1. Copy snippet from ./Fan/dsdt-edit.txt
