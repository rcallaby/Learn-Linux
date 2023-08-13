# Determining Disk Usage for Files and Folders

There may be instances where knowing the size of various folders and files comes in handy. If you have been using a computer for a number of years I don't need to explain to you the reasons why this is helpful. As well, many times these commmands are used as a question for a technical interview and honestly you should definitely know these commands by heart if you ever plan on getting hired in a real world job.

That being said, detrmining diek usage for files and folders is quite easy. As well, the command is pretty easy to remember so it shouldn't be difficult to pass any technical interview or even a certification exam question if this topic comes up. That being said I will discuss how to determine disk space for files and folders below.

The first command to check disk usage in Linux is the df command, this stands for disk free or the amount of free space you may have on your hard drive or if you specify a folder then how much free space may be available in that folder.

You can use this command in the following way:

```
    df
```
Or alternatively, you can get it in human readable format by using the -h switch such as the following:
```
    df -h
```
By human readable format you get the output in kilobytes, megabytes and gigabytes.

You can also specify a specific file system by using the following:
```
    df -h /dev/sda2
```
If you want to inspect the mount point or the point where your hard drive starts you could use the following:
```
    df -h /
```
The backslash at the end specifies the root folder or the mount point for the main hard drive. It is assumed to be the main hard drive unless you specify a specific folder or drive on your system.

You can list all file systems by type by using the df command such as the following:
```
    df -ht ext4
```
You can subsitute any file system that may be on your system such as FAT32 or NT or even ext3. Now, what file systems you may have on your computer is unknown to me so just use your judgement on how best to use this command.

You can check disk usage by using a very easy command to remember, the du command. As you can imagine the du command stands for disk usage command.

You can use it in the following manner:
```
    du
```
As well, you can also make it in a human readable format such as the following:
```
    du -h
```
You can determine how much size a disk is using by simply typing in the following:
```
    du -hs
```
You can also figure out how much space a directory taking up by using the following:
```
    du -hs /Desktop
```
Or alternatively, if you wanted to find out how much space the /etc directory is taking up you could just simply type in the following:
```
    du -hs /etc
```

Now, depending upon the security settings of your system you may have to type in sudo before you type in any of the following commands. Some network administrators lock down their networks pretty tightly so you may need root or admin privileges in order to use these commands. Please keep that in mind when using these commands and also for any certification or technical interview questions.