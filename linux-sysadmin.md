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

### Shared Libary 
- Files containing functionality that other applications can use
- These files end in a '.so' extension for "shared object"
- Found in the following locations on a linux system:
  - /lib
  - /usr/lib64
  - /usr/local/lib
  - /usr/share
- Two types of library files:
  - Dynamic (ends in .so)
  - Statically linked (ends in .a)
 #### Managing Shared Libraries
  - ldd: prints out shared object (library) dependencies
  - ldconfig: configures dynamic linker run-time bindings, creates a cache based on library directories and can show you what is currently cached
  - /etc/ld.so.conf: configuration file that points to directories and other configuration files that hold references to library directory locations
  - LD_LIBRARY_PATH: Legacy environment variable that points to a path where library files can be read from 

### yum commands:
 - yum update:  searches online repositories for updated packages compared to what is currently installed on the system, upgrades packages
 - yum search: search the yum repositores for a specified package
 - yum info: list information about a specified pakcage
 - yum list installed: displays all installed packages
 - yum clean all: cleans up all of yum's cache information and its local database file
 - yum install: installs a specified package and all of its dependencies
 - yum remove: uninstalles a package, leaves dependencies behind
 - yum autoremove: uninstalls a package and its dependencies
 - yum whatprovides: find out what package provides a specified file name
 - yum reinstall: reinstalls a package
 
 ### Red Hat Package Manager (RPM):
  - The .rpm package contains:
    - Application or utility
    - Default configuration files
    - How and where to install the files that come with the package
    - Listing of dependencies that the package requires
  - The rpm database:
    - Located in /var/lib/rpm
    - Use the rpm --builddb command to repair a corrupted rpm database
  - Dependencies need to already be installed, or installed with the package
    - yum handles dependencies for you, rpm does not
  #### rpm commands:
    - rpm -qpi: displays information on a package 
    - rpm -qpl: lists files in a package
    - rpm - qa: lists out all installed packages
    - rpm -i: installs a specified package, often combined  with other options to provide more verbose output, i.e rpm -ivh
    - rpm -U: upgrades an installed package with a newer version
    - rpm -e: uninstalls (erases) an package
    - rpm -Va: verify all installed packages
    - rpm2cpio: converts an .rpm file into a cpio archive file, often combined with the cpio command, i.e. rpm2cpio some.rpm | cpio -idmv

### MBR Partitioning Tools
 - lsblk: command used to list out block devices (such as hard drives)
 - fdisk: Legacy command used to create partitions of the MBR (DOS) type
 - parted: modern command used to create partitions of MBR or GPT types.
 Partitions ID's:
  - 83 - standard linux filesytems
  - 82 - Linux swap partitions
  - 8e - Linux LVM volumes
 
### GPT Partitioning Tools
 - gdisk: This is a command in the style of 'fdisk' that can be used to create GPT partitions on disks
 - parted: The parted command can be used to create both MBR and GPT disk partitions
 
### Swap Partitionging Tools
 - fdisk, gdisk, parted: any of these tools can be used to create swap partitions.
 - mkswap: This command is used to format a partition to be used as swap space.
 - swapon: Enables a swap partition or file
 - swapoff: Disables a swap partition or file.

### Linux File Systems
 #### Non-Journaling:
   - ext2 - legacy linux file system, releasted in 1993
 #### Journaling:
   - Uses a journal to keep track of changes that have not yet been written to the file system.
   - Examples:
      - ext3 - released in 2001, introduced journaling to ext2
      - ext4 - released in 2006, added extra features, meant to be a 'stop-gap' until a better solution comes along
      - XFS  - created in 1993 by Silicon Graphics, inc. For the IRIX operating system. Ported to Linux in 2001

### File System Utilities
 - mkfs: creates a new file system on a partition, Can be used like so:
    - mkfs -t [fs-type]
    - mkfs.[fstype]
 - blkid: displays the file systems universally unique identifier (UUID)

### Disk usage
 - df: command that show the available disk on a file system
 - du: command that displays the amount of disk space in use
 - inode: an inode (index node) stores information about files and folders, such as: permissions, ownership and file type. Most file systems contain a maximum number of inodes that it can contain.
 commands that display inode information:
  - ls -i
  - df -i
  - du --inodes

### File System Maintenance
 - fsck: file system check utility, can be invoked via command line and configuration in /etc/fstab. Devices must be unmounted before a check can run.
 - e2fsck: file system check utility for ext2, ext3, and ext4 file systems, can be used to replay the file systems's journal
 - mke2fs: utility for creating new ext2, ext3 or ext4 file systems.
 - tune2fs: Utility used to adjust parameters on a ext2, ext3, or ext4 file system
 
### Mount Commands
 - mount: Command used to mount a file system to a mount point (directory).
 - man mount: Manual pages for the mount command. Pay particular attention to the file system independent mount options.
 - unmount: Command used to unmount a file system. Can specify either the device, label, or mount point (directory)
 - /etc/fstab: file system table file. Permanent mount configurations are set here.
   
### Permissions
 #### Permissions are broken down into three categories:
    user group other/world
    - Symbolic Permissions:
       r: read 
       w: write
       x: execute
       -: no permission
    - Octal Permission:
       4: read
       2: write
       1: execute
       0: no permission
### Modifying Permissions:
 - chown: change the ownership of a file or directory
 - chmod: Change the mode of a file or directory
 - chgrp: Change the group ownership of a file or folder
 
### Advanced Permissions:
 - SUID: The 'set uesr id' bit. FIles with an 's' in the place of the 'x' permission within the user's column have this set. Note that this will not work on Bash scripts anymore. Also, many file systems can be mounted with the 'nosuid' option/
 - SGID: THe 'set group id' bit. Files and folders with the 's' in the place of the 'x' permission within the groups's column have this set. This assigns group ownership to files. Useful for shared group directions.
 - Stick Bit: This permission has a 't' in place of an 'x' in the other's column. This permission only allows the creator of a file to remove the file.
