# KTPocket KT-R1
# GammaOS + GammaOS Lite Custom Firmware - v1.5.1


Download and instructions
----------------------------
- GammaOS v1.5.1 download: https://github.com/TheGammaSqueeze/GammaOS-MTK/releases

Instructions:
- [Brand new install (Flashing from Stock KT-R1 Firmware. Bootloader never unlocked before, flashing via fastbootd)](https://github.com/TheGammaSqueeze/GammaOS-MTK#instructions---brand-new-install-flashing-from-stock-kt-r1-firmware-bootloader-never-unlocked-before-flashing-via-fastbootd)
- [Help! My device is no longer booting! Or I want to go back to Stock OS!](https://github.com/TheGammaSqueeze/GammaOS-MTK#help-my-device-is-no-longer-booting-or-i-want-to-go-back-to-stock-os)

Information
----------------------------
GammaOS is based on LineageOS 19.1 (Android 12). It provides a debloated and performance optimized experience for users who are looking to get the best out of their KT-R1 devices.

Features:
- Based on debloated and clean LineageOS 19.1 build, Android 12 for a smoother experience. GammaOS includes Google Services and Play Store. GammaOS Lite excludes Google apps and services for extra performance headroom.
- Daijisho launcher as front-end, pre-configured with RetroArch for some systems. (Optimized settings for GB,GBC,GBA,NES,SNES,Genesis,PSX) (BIOS files need to be supplied by you).
- Aurora store included.
- Quick settings tiles for Performance modes, ABXY layout changes, Adjusting analog stick sensitivity, invert axis for analog left/right, swap dpad and left analog input.
- Adguard ad blocking included as default (can be disabled via Private DNS settings).
- Magisk/root included.
- 60hz refresh rate fix for display, color calibration to remove green tint and increase vibrance.
- CPU, GPU, Memory now using performance governors for extra performance boost.
- L2/R2 fixed for apps and games with issues with those buttons.

Other Information:
- RetroArch hotkey: Back button
- RetroArch menu toggle: (L3 + R3 or Back button short press). Choosing Close Content option closes the game.
- RetroArch shortcuts (Hold hotkey down) + L1 = Slow Motion | L2 = Load State | R2 = Save State | R1 = Fast Forward | X = Show FPS | Y = Screenshot
- Auto save state then quit RetroArch: Hold down Back. Auto loads save state when launching a game again.
- Back button + right analog stick up/down to adjust brightness.

What's missing:
- Built-in button to on-screen mapping software, alternative solutions can be found in app store.
- Bluetooth Audio Support
- 3.5mm audio support (can use USB-C headphones/adapters instead)


Instructions - Brand new install (Flashing from Stock KT-R1 Firmware. Bootloader never unlocked before, flashing via fastbootd)
----------------------------

Prerequisites:
- Extract the GammaOS/GammaOSLite folder and its files before proceeding.
- Get ADB and Fastboot tools + drivers.

**On Windows**

- Ensure you install the Universal ADB Driver: https://github.com/K3V1991/ADB-and-FastbootPlusPlus
  - Ensure both these boxes are ticked during the install
  - ![image](https://github.com/TheGammaSqueeze/GammaOS-MTK/assets/116582950/3188d5ca-c1ec-4073-a979-f1c9483ccdba)


- Install Mediatek Drivers (included in the release zip in the MTK_USB_DRIVER folder). Run the Mediatek_Driver_Auto-Installer_5.1632.00.exe program.

- Install Unisoc Drivers (yes, that's right), run the DPInst64.exe program in your relevant OS folder. (Available here: https://github.com/TheGammaSqueeze/GammaOS/releases/download/GammaOS_v1_RG405M/UnisocDrivers.zip, Win10 drivers will also work on Win11.)

- Remove/rename any existing fastboot.exe application that exists on your PC to prevent issues with flashing such as the flashing stalling at vbmeta_a. Open a command prompt, type in the following command: where.exe fastboot.exe. This will show you where your fastboot.exe is being called from. Anything that is not in the C:\Program Files (x86)\ADB and Fastboot++\fastboot.exe location should be renamed to something else. Rename to something like oldfastboot.exe

**On MacOS**: Install homebrew: https://brew.sh/

Via homebrew on **MacOS**:
- `brew update`
- `brew install android-platform-tools`

The process **on Linux** differs from distro to distro.

On Arch, you can use the `android-sdk-platform-tools` from AUR.

On Garuda, simply run `sudo pacman -Syu android-sdk-platform-tools` since it has Chaotic-AUR preinstalled.

**On the KT-R1** device itself:
- Enable USB Debugging on the KT-R1: https://developer.android.com/studio/debug/dev-options
- **In the same Developer Options you enable USB debugging in, enable OEM unlock.**

Unlocking bootloader:
- Connect your KT-R1 to your PC via USB cable while booted into Android, open a command prompt/terminal window, and issue the following command:
  `adb reboot bootloader`
- Your KT-R1 will reboot, and you will see the text "fastboot mode" on the bottom left of the screen 
- In your command prompt/terminal window, issue the following command: `fastboot flashing unlock`
- On your KT-R1, you will have 3 seconds to press to volume up button to confirm that you want to unlock the bootloader. Press this.
- You will see in the command prompt/terminal that the unlock is complete, as well as on the device itself.

Flashing the custom firmware:
- Close all command prompt windows from before
- Navigate to your extracted GammaOS/GammaOSLite folder
- Open the FlashPartitions script 
  - Windows: double click the .bat file. 
  - Mac/Linux, open a terminal in the GammaOS directory, issue the command `sh FlashPartitions.sh`
- It will begin flashing the firmware. This step can take up to 10 minutes so be patient.
- Open the EraseUserData script
  - Windows: double click the .bat file. 
  - Mac/Linux, open a terminal in the GammaOS directory, issue the command `sh EraseUserData.sh`
- It will begin factory resetting your device in preperation for GammaOS. When the script is complete, the command prompt window will close itself after 60 seconds.
- You can now reboot your KT-R1 by pressing the power button once.
- Your device will reboot, and will stay at the KTPocket logo for about 2 minutes before booting into the new firmware for the first time. Reboots after this will be much quicker. Do not be alarmed by the debug messages warning about unlock and skip verify, this is normal after unlocking the bootloader
- Congratulations, you are now on GammaOS!
- **There is also an additional experimental graphics driver which can boost performance further, install this Magisk module: https://github.com/TheGammaSqueeze/GammaOS-MTK/releases/download/GammaOS_v1.5.1/experimental-ktr1-malidriver-r38p1.zip**
  
- **Don't forget to open the kLauncher app on your KT-R1 to set your joystick/ABXY layout, and to calibrate your sticks! Make sure to grant root access when opening the app when requested.**


https://github.com/TheGammaSqueeze/GammaOS-MTK/assets/116582950/52477fc6-5f17-4871-920b-c3d373490f4f



- **You may also want to install the Yuzu Controller fix Magisk module to ensure you don't have issues controlling games in Yuzu or other games. Magisk module here: [https://github.com/TheGammaSqueeze/GammaOS-MTK/blob/main/rgp2xbox_ktr1_yuzu_fix.zip](https://github.com/TheGammaSqueeze/GammaOS-MTK/raw/main/rgp2xbox_ktr1_yuzu_fix.zip) Install and restart.**


https://github.com/TheGammaSqueeze/GammaOS-MTK/assets/116582950/7ed50312-4c4b-448b-9ec3-47c4f1df8d6e



Help! My device is no longer booting! Or I want to go back to Stock OS!
----------------------------

The stock firmware can be downloaded here: https://drive.google.com/file/d/1SD--Ns0wbqkyk8FqrhD4hCi8Jgj3Sspy/view?usp=sharing

Instructions:
- Extract the zip file
- Install Mediatek Drivers (included in the zip in the MTK_USB_DRIVER folder). Run the Mediatek_Driver_Auto-Installer_5.1632.00.exe program.
- Open the SPFlashToolV6.exe application in the SP_Flash_Tool_V6 folder.
- For the Download-XML, click the Choose button, then navigate to the location where you extracted the zip file. Choose the file: G98_230726/download_agent/flash.xml
- In the dropdown option under the Download button, change this to Format All + Download. Ensure Auto Reboot is ticked under BROM Connection on the left:
![image](https://github.com/TheGammaSqueeze/GammaOS-MTK/assets/116582950/60db5448-12e5-4d57-9262-ff49e1b90014)

- When ready to flash the stock firmware, press the Download button.
- Plug in your USB cable to your KT-R1, and hold down the power button until you see the progress bar move at the bottom of the application.
- Once complete, your KT-R1 will automatically reboot into the stock firmware.

You can also follow this guide and download from the KTPocket Discord server (https://discord.gg/vcneCAvM):
https://discord.com/channels/971941186120060938/1134310003155664906/1191648409719930880
