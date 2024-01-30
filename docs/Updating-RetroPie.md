|Version|
|---|
|4.8|

# Updating RetroPie

The conventional way to update RetroPie and install new features is through the setup script.     
The setup script can be accessed from the **RetroPie menu** in EmulationStation. 

It can also be accessed from the terminal with `sudo ~/RetroPie-Setup/retropie_setup.sh`.

**NOTE**: any updates require the RetroPie system to be **online**, otherwise downloading and installing the files required in the process will not work.
 
**Before making any major updates it is important to make backups just in case [(see backup options below)](#making-a-backup).**

## Update All Installed Packages

![update](https://user-images.githubusercontent.com/540857/106713057-e03e2b00-65c7-11eb-9529-766986334e8b.png)

- **Basic Install:** This is intended as a first install and is not required if using a pre-built image. eg When installing RetroPie on top of an existing OS.
- **Update:** This will update the RetroPie-Setup script and all installed packages.
- **Manage Packages:** This will allow you to install and update individual emulators, ports, controller drivers (like the ps3 or xboxdrv) other optional packages.
- **Configuration / Tools:** Configuration and tools including BlueTooth and WiFi setup, splashscreens and theme. You can also access any packages that have additional configuration here.
- **Update RetroPie-Setup Script:** Updates the RetroPie-Setup script to the latest version.
- **Uninstall RetroPie:** Uninstalls RetroPie from the system.
- **Reboot:** Reboots your system.

## Manage Packages

![manage](https://cloud.githubusercontent.com/assets/10035308/17757080/913dbf7e-64a1-11e6-8370-05a3d2a720ed.png)

- **Core:** These are essential packages needed for RetroPie to run. Do not remove them.
- **Main:** These are the main emulators that come installed with the RetroPie SD image.
- **Optional:** These are optional packages that are working but aren't included with the RetroPie SD image.
- **Drivers:** Here you install gamepad drivers like the PS3 or Xboxdrv.
- **Experimental:** These packages have not been fully tested and may have bugs.
 
## Manage Core Packages

![core packages](https://cloud.githubusercontent.com/assets/10035308/15919781/a18d06ca-2dd1-11e6-9cec-136fc5f0e727.png)

Each section of the manage packages portion of the setup script have the option to install/update all packages and remove all installed packages. You can also update/install and remove packages individually.

The core components needed for RetroPie to function are:

- **RetroArch:** Frontend for the Libretro api, necessary for most emulators to run.
- **EmulationStation:** Frontend for sorting and launching all of your games.
- **RetroPie Menu:** Menu in EmulationStation for simpler configuration of your system.
- **Runcommand:** The Runcommand launch menu that assists launching your games with proper configurations, see the related documentation page [HERE](Runcommand).

## Updating/Installing individual packages

You can update/install and remove packages individually.

When selecting a package there is also a help guide with extra information specific to that package:

![individual](https://cloud.githubusercontent.com/assets/10035308/15987047/5414269a-2fd8-11e6-87ff-a0021e244054.png)

### Package Help

![package_help](https://cloud.githubusercontent.com/assets/10035308/15987048/542d760e-2fd8-11e6-909f-827b120dfc34.png)

The Package Help for each emulator should show you:
- The name of the package
- ROM extensions
- ROM folder
- BIOS filename and folder if applicable

## Binary vs Source updates

### Binary
Updating from binary gets the pre-compiled version of the package(s). It is fast, and will typically be a known-good version. Binaries are typically updated every RetroPie release. It is the recommended method to install/update unless you have a specific reason for needing the latest bleeding-edge version. 

**Note:** Binary versions are not available for all platforms/packages.

### Source
Updating from source downloads the latest source code, and builds the binary directly on your system. This takes much longer - hours, even days, depending on the system and package(s). It is suggested only if you require a specific fix that is not available as a binary.

## Latest SD image

If you are worried about conflicts during an update you can always just start with the latest fresh sd image which can be downloaded [**here**](https://retropie.org.uk/download/) and just copy all your files back over onto that instead of updating from an older image.

## Making a Backup

### Backup Option 1

You can create an sd image of your current sd card with [win32diskimager](http://sourceforge.net/projects/win32diskimager/files/Archive/) (if you're on windows)

- Plug your sd card into your laptop (you will need a sd card reader for this)
- Open win32diskimager as an administrator (you can right click on it to run as an administrator)

![runasadministrator](https://cloud.githubusercontent.com/assets/10035308/10266141/babb3420-6a0c-11e5-9f20-c26297b9fbbf.png)

- make sure you have the correct drive letter for your SD card! 
- define the file path that you want to save your .img backup as

![win32diskimager](https://cloud.githubusercontent.com/assets/10035308/10266156/79baadf6-6a0d-11e5-9c98-62211328c68a.png)

- Click **read** to create your backup. (after you've backed this image up if you screw something up later and want to start from this image you can just click write and it will write this sd image back to your sd card.)
- note if you have a 64GB sd card it will create a 64GB backup file even if you don't have it completely filled up. If you don't want a file that large see the next option. 

Note: images created this way can only be written to a microSD card of the EXACT same size or bigger.  As an example you may not be able to write an image of a 64GB microSD onto another 64GB card. That's because actual real usable space may vary by manufacturer and in some cases even with the same manufacturer. To avoid this issue you can use option 3.

### Backup Option 2

if you don't want to create a sd image you can just back up your bios, roms, and configuration files from the samba shares

![samba](https://cloud.githubusercontent.com/assets/10035308/12865893/d2eab264-cc77-11e5-9ec6-003e13322a5a.png)

### Backup Option 3 (transferring to another SD)

You can use **Rpi-clone**, a shell script that runs directly on your Raspberry Pi. Requires a USB microSD card reader.
Detailed instructions [here](https://github.com/billw2/rpi-clone).

### Backup Option 4 (macOS)

Open a terminal window and type `diskutil list`. A list of all hard disks and partitions shows up. Find a partition with the name `boot` or `bootfs` - it should say _(internal,physical)_ beside the `/dev/disk#`. Example:

``` sh
    user@host$ diskutil list  
    /dev/disk0 (internal, physical):  
    #:                       TYPE NAME                    SIZE       IDENTIFIER  
    0:      GUID_partition_scheme                        *500.3 GB   disk0  
    1:                        EFI EFI                     209.7 MB   disk0s1  
    2:          Apple_CoreStorage Mac HD                  499.4 GB   disk0s2  
    3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3  
    /dev/disk1 (internal, virtual):  
    #:                       TYPE NAME                    SIZE       IDENTIFIER  
    0:                  Apple_HFS Mac HD                 +499.0 GB   disk1  
                                      Logical Volume on disk0s2  
                                      3BAC0F9E-19F8-4AAB-8752-6514B573B497  
                                      Unencrypted  
    /dev/disk2 (internal, physical):  
    #:                       TYPE NAME                    SIZE       IDENTIFIER  
    0:     FDisk_partition_scheme                        *15.9 GB    disk2  
    1:             Windows_FAT_16 boot                    59.8 MB    disk2s1  
    2:                      Linux                         15.9 GB    disk2s2  
```


  In this case `/dev/disk2s1` (partition 1) is named `boot`. That disk# is the RetroPie SD card - in the example it is `/dev/disk2`. Confirm that the size (on the right) matches the size of your SD card.
 
  Type `cd ~ ; sudo dd if=/dev/rdisk2 of=backup.img bs=1m` to write a disk image to your home directory. Note that you need to use the entire disk (`/dev/disk2`) and not just a partition (`/dev/disk2s1`).
