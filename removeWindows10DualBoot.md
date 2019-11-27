# Remove Windows 10 DualBoot and GRUB Bootloader
If you have Windows 10 and Linux installed, and you want to remove Linux, here is a short description about how to do that.

### Note
* You should backup all your important data from the Linux system, otherwise they will be lost. Do also backup important files from Windows.
* I do not accept any liability for damage to your computer system or loss of data that results from your use of this instruction.

### Definition
* **GRUB** = Grand Unified Bootloader
* Instead of "**Volume**" you can also say "**Partition**"

### GRUB Console:
This is how the GRUB-Console looks like:

![https://praxistipps-images.chip.de/xFV0Cn6g9XnW7pQAwIBvaS_fYxE=/0x0/filters:format(jpeg):fill(000,true):no_upscale()/praxistipps.s3.amazonaws.com%2Fdie-grub-rescue-kommandozeile-startet-statt-windows-10_000f7e4d.png](https://raw.githubusercontent.com/Dennis2512/Windows10DualBootRemoval/master/image_assets/grub.png)

### Delete Linux:
* Open **Windows Disk Management** by pressing `Windows + R` and typing in `diskmgmt.msc`
* Find the volume where **Linux** is installed on and find the volume for the **Linux Swap Area**
* Volumes belonging to Linux often do not have any entries below "File System"
* Right click both volumes and select `Delete Volume...`

### Locate and remove GRUB
* If you have Windows Disk Management still opened, check volume "Status" and remember that one with "EFI" in it
* GRUB is located in the "EFI-Volume"
* Run `cmd` as Admin
* Type in `diskpart`
* Type in `list disk` to list all disks
* Type in `sel disk <disk number>` to select the specific hard disk
* Type in `list vol` to list all available volumes
* Type in `sel vol <vol number>` and choose the "EFI-Volume" 
* Type in `assign letter=Z:` (or any other not assigned letter) to make the volume visible in the Windows Explorer
* Run `cmd` as Admin
* Type in `cd /d <name of the assigned letter>:`
* Type in `dir` to see the EFI volume folder
* Type in `cd EFI` to go into the EFI directory
* Type in `dir` again to show all available directories, you should see your installed Linux Distribution as one of them
* To delete this folder, type in `rmdir /s <name of linux directory>` and confirm your action by typing in `y`
* If you now type in `dir` again, the folder should be gone
* Now, restart you computer and **Windows will boot instantly**

You have now successfully removed DualBoot off your Windows 10 PC.
