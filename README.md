# Dell-Latitude-5300-2-in-1-Hackintosh-OpenCore-Bigsur-Sonoma
step by step guide to hackintosh your dell latitude 5300 2in 1

## Specifics

- CPU : Intel® Core™ i7-8665U Processor
- Graphics : Intel® UHD Graphics 620
- Memory : Samsung LPDDR3 32GB 1867MHZ (16GB * 2 Dual Channel)
- Display : 13.3 Inch 1920 X 1080 (WUXGA+) 3:2 10 Points Multi Touch
- Sound : Realtek ALC3253 (ALC225)
- Samsung NVMe SSD 512GB
- WiFi/Bluethooth : Intel ax200
- Battery : 42WHr


## BIOS Version / OpenCore Bootloader Version / macOS Version Supported

- OpenCore Bootloader : v0.9 and Above
- macOS : Big Sur 11.7.10, Monterey 12.7, Ventura  13.6, Sonoma 14.1.1


## BIOS Setup

- Load Optimized Defaults

## Hackintosh Status:

Touch enabled OS PICKER ✅ 
WIFI/BT : ✅ 
GPU acceleration : ✅ 
Touchscreen : ✅ working as a magic mouse 2 with gestures 
Dell pen : ✅ working as a magic mouse 2 with gestures 
Keyboard : ✅ 
Trackpad : ✅ 
Sound and mic : ✅ 
HDMI  : ✅ 
Usb type A : ✅
camera : ✅
 Usb type C + (video output) : ✅ + ✅

SMBIOS : Macbook15.4

## Step by step how to :

# 1st Step is to boot Big sur (Please Read the FULL guide before starting)
 - YOU Must install Big sur first before upgrading Sonoma
 - Follow dortania guide to make bootable usbstick for BIG SUR 11.7 macos (not montery/not ventura)  : https://dortania.github.io/OpenCore-Install-Guide/installer-guide/
# 2nd Step copy Big Sur EFI to usb
 - copy Efi folder (inside 1 - EFI BIG sur) to usb stick root.
 - now your usb root should have 2 folders {com.apple.recovery.boot & EFI}

<img src="https://dortania.github.io/OpenCore-Install-Guide/assets/img/com-efi-done.a6fb730e.png" alt="">

# 3nd Step config.plist config
 - download ProperTree and GenSMBIOS.

            -   https://github.com/corpnewt/ProperTree
            -   https://github.com/corpnewt/GenSMBIOS
            
 - Next, let's open ProperTree and edit our config.plist:

    * ProperTree.command
      ** For macOS
    * ProperTree.bat
      ** For Windows

    Once ProperTree is running, open your config.plist by pressing Cmd/Ctrl + O and selecting the config.plist file on your USB.

 - For setting up the SMBIOS info, we'll use GenSMBIOS application.

    
    <img src="https://dortania.github.io/OpenCore-Install-Guide/assets/img/smbios.35dd8ead.png" alt="">

    Run GenSMBIOS, pick option 1 for downloading MacSerial and Option 3 for selecting out SMBIOS. 
    This will give us an output similar to the following:

        #######################################################
        #               MacBookPro15,2 SMBIOS Info                  #
        #######################################################

        Type:         MacBookPro15,2
        Serial:       C02KCYZLDNCW
        Board Serial: C02309301QXF2FRJC
        SmUUID:       A154B586-874B-4E57-A1FF-9D6E503E4580


        The Type part gets copied to Generic -> SystemProductName.

        The Serial part gets copied to Generic -> SystemSerialNumber.

        The Board Serial part gets copied to Generic -> MLB.

        The SmUUID part gets copied to Generic -> SystemUUID.

        We set Generic -> ROM to either an Apple ROM (dumped from a real Mac), your NIC MAC address, or any random MAC address (could be just 6 random bytes, for this guide we'll use 11223300 0000. After install follow the Fixing iServices ( https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html ) on how to find your real MAC Address)

        Reminder that you need an invalid serial! When inputting your serial number in Apple's Check Coverage Page , you should get a message such as "Unable to check coverage for this serial number."

        Automatic: YES

        Generates PlatformInfo based on Generic section instead of DataHub, NVRAM, and SMBIOS sections
        #Generic

# 4nd Step Booting the OpenCore USB

     - boot usb stick and finish instalation.

# 5nd Step : OpenCore Post-Install
     - follow this guide to Booting without USB and Fixing iServices
     
     https://dortania.github.io/OpenCore-Post-Install/#how-to-follow-this-guide

# 5nd Step update to Sonoma
    
     - Update from settings but before rebooting make sure to replace EFI folder with corresponded files .
