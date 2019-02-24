### Main File system locations
- mount: can be used to mount partitions to directories, or show all existing mounts without any options
- lsblk: Used to show all block devices ona system and their names
- fdisk -l /dev/diskname: can be used to list out partition information on the specified disk
- swapon --summery: shows a summayr of the swap usage on a system, same information can be found in /proc/swaps


### LVM (Logical Volume Manager)

 #### Allows the creation of "groups' of disks or partitions that can be assembled into a single (or multiple) filesystems:
  - Can be used for nearly any mount point Except /boot
  - Flexibility -allows for resizing of volumes
  - Snapshots - allows for "point in time" copies of your logical volume
 #### Sampling of LVM Commands:
  - pvs: lists out the physical volumes in an LVM group
  - vgs: lists out volume groups within an LVM group
  - lvs: lists out the logical voumes within an LVM group
 
### Differences between MBR and GPT

 #### MBR (Master Boot Record):
  - Traditionlly supported only 26 total partitions (4 Partitions, with one partition extended to 23 partitions)
  - Partition size limited to 2TB
 #### GBT (GUID Partition Table):
  - Supports 128 partitions
  - Partition size up in the ZB (zettabyte) range
  - Needs UEFI (Unified Extensible Firmware interface) to boot:
    - Replacement for traditional BIOS, can act in legacy BIOS mode
    - Requires a 64bit operating sytem
    - Prevents unauthorized operating systems from booting on the system

### GRUB2 Configuration Commands:
- grub2-editenv list: view the default boot entry for the grub configuration file
- grub2-mkconfig: creates (or udpates) a /boot/grub2/grub.cfg file based on entries from the /etc/default/grub file (on Debian systems, the '2' is omitted from the command name. e.g.grub-mkconfig)
- update-grub: command that can be used to update a GRUB2 configuration after changes to /etc/default/grub have been made, found on Debian based systems
