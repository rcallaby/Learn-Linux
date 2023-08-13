# Navigating in Linux

You can navigate in the Linux file system by using a variety of commands, some of which we covered in the quick start lecture of this course.

For instance to determine where you are in the directory you would use the pwd command as follows:
```
    pwd
```

To see the contents of the directory you would use the ls command and that has a variety of switches such as
-a which shows hidden files and directories such as:
```
    ls -a
```
-s which shows file size such as:
```
    ls -s
```
-l flag is for the “detailed” view of the contents, you can view file permissions, file ownerships and so on such as:
```
    ls -l
```
-S sorts files by file size such as:
```
    ls -S
```
-t sorts by time and date such as:
```
    ls -t
```

If you combine the flags together you can use to get detailed information on all hidden files and directories such as
```
    ls -la
```


You can change directories by using the cd command such as:
```
    cd <directoryname>
```
For instance you can move about in the home directory by typing cd Documents which would take you to the Documents folder

To move up one level you would use the cd .. command such as:
```
    cd ..
```
You can also move up two directories by using the cd ../.. and that will transverse two directories such as this:
```
    cd ../..
```
Using the command less you can view the contents of the files such as:
```
    less
```
