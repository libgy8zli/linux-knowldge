### Main File system locations
- mount: can be used to mount partitions to directories, or show all existing mounts without any options

- lsblk: Used to show all block devices ona system and their names

- fdisk -l /dev/diskname: can be used to list out partition information on the specified disk

- swapon --summery: shows a summayr of the swap usage on a system, same information can be found in /proc/swaps


### LVM (Logical Volume Manager)
Allows the creation of "groups' of disks or partitions that can be assembled into a single (or multiple) filesystems:
 - Can be used for nearly any mount point Except /boot
