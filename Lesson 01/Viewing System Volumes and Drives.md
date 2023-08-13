# Viewing System Volumes and Drives

When using Linux is helpful at times to view what drives or partitions you have on your system. There are mulitple ways to accomplish this, and I will show you some of these commands in this tutorial. These commands may or may not be in the video portion of the course, so that is why it is also very helpful to refer to written documentation as well as video documentation while taking a course.

Now, these commands may require you to have admin or root access in order to view the system volumes and drives. That means at the very minimum you should be using a user that has sudo privileges. To check to see if you can use sudo you could use the following command:

```
    sudo -l
```

One of the most useful ways to determine system volumes and drives is to use the lsblk command. As you can imagine the lsblk command is a off shoot of the ls command we have covered earlier in this course. To use it then you would just simply type in the following:

```
    lsblk
```

If you want a detailed view of the filesystems you would use the -f switch such as the following:

```
    lsblk -f
```

This shows both the name of the partition or drive and the filesystem type. Linux is capable of handling many types of file systems so having that knowledge may be handy in the future especially if you are trying to diagnose an issue with a hard drive or system volume not operating as expected.

Now, as I mentioned above there are multiple ways to accomplish the same thing in Linux. That is actually helpful to know because if you forget one command there are other commands to you can remember to accomplish the same task. For instance, as I mentioned above the lsblk is an offshoot of the ls command but you can just simply use a variation of the ls command to get the same information such as the following:

```
    ls -IF /dev/disk/by-id
```
As well, you can see how hard drives are partitioned using the following command:

```
    blkid
```

Now, this is a listing of some of the commands you can use to get informtion on system volumes and drives in your Linux operating system. You may or may not need to install some of these commands if they are not already a part of your system. As well, if a command does not work for any reason the first thing you should do is to add sudo in front of it as you may need to have admin or root privileges in order to perform these commands.

