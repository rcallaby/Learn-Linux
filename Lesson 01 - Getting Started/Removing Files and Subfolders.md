# Removing Files and Directories in Linux

Obviously if you created a file or a directory you would like to also know how to remove a file or directory.
It just goes hand in hand.

To remove a file you would just simply type rm and then the file name. Such as:
```
    rm filename
```

You can also remove multiple files by typing multiple file names so 
rm file1 file2 file3 would delete all of those files at once such as:
```
    rm file1 file2 file3
```

If you wanted to remove a directory and all of the files in that directory you could just type 
rm -r directoryname and that will remove all the files and the directory name such as:
```
    rm -r <directoryname>
```
Now keep in mind that rm -r <directoryname> also works on all sub directories and all sub files.

Tt would remove everything in those so be careful if you want to keep any files in the subfolders to not use this command without first moving those files to a different directory

To remove a empty directory you would use rmdir such as:
```
    rmdir <directoryname>
```

The trouble with using rmdir is that the directory has to be empty in order for you to use it.

This also includes hidden or system files.

Now remember you can find if you have hidden or system files by using ls -a switch to see all of the files in the directory including the hidden files such as:
```
    ls -a
```

