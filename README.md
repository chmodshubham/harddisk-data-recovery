# Data Recovery from SSD/Harddisk

Recovering deleted files or folders from a server can be a complex task, especially if the server is not set up with a trash or recycle bin system. Here are some general steps you can follow:

If the files are deleted using `rm -rf` then forget about them and focus on not repeating the mistake.

#### 1. Stop using the system

As soon as you realize that you've deleted a file or folder, stop using the system. When a file is deleted, the space it occupied is marked as free and can be overwritten by other data. By continuing to use the system, you risk overwriting the deleted files and making them unrecoverable.

#### 2. Use a File Recovery Tool

There are several file recovery tools available for Linux systems. One of the most popular is `extundelete`.

To install `extundelete`, use `sudo apt-get install extundelete`

##### Identify the correct device

Use the `lsblk` or `df` command to identify the device identifier of the hard disk or SSD.

##### Unmount the device

Use the `umount` command to unmount the device. This is to prevent any further changes to the data on the device while we are trying to recover the deleted files.

```bash
# Replace /dev/sdb2 with your actual device if it's different.
umount /dev/sdb2
```

![image](https://github.com/ShubhamKumar89/hard-drive-backup/assets/97805339/15347b0b-85c4-4230-84a5-6e19755cf22f)

##### Filesystem Corruption Check

Run `fsck` on the filesystem with `sudo fsck /dev/sdb2` to fix any issues that `fsck` finds.

##### Recover the data

 Use this command to recover a deleted directory:

 ```bash
sudo extundelete --restore-directory /path/to/deleted/directory /dev/sdb2
```
 
This option will attempt to recover all deleted files from the filesystem. Be aware that this could recover a large number of files and take a long time.

```bash
sudo extundelete --restore-all /dev/sdb2
```

![image](https://github.com/ShubhamKumar89/hard-drive-backup/assets/97805339/f8711c18-f5e7-4775-a673-39de85381bbf)

![image](https://github.com/ShubhamKumar89/hard-drive-backup/assets/97805339/3d2faccd-58a9-460e-a922-c0db77f1070f)
