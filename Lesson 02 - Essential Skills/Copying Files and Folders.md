<strong>Copying Files and Folders</strong>

In Linux the way to copy both files and folders only one command is needed. This command is known as the cp command. Of course, there are multiple ways to do this in Linux but for the sake of simplicity only the cp command is going to be discussed in this article.

The way to use this is with a very simple command such as the following:
```
    cp [filename] [filenamecopy]
```
By default the cp command runs in the same directory unless otherwise specified. IF you try and make a copy of a file with the exact same name you will get an error message. So therefore it is best to try and make the other filename different by either adding a different extension or some other way of differentiating it from the other filename.

Now, like other Linux commands the cp command seems to very simple but it is also very powerful. For instance, you can use it in a verbose manner, or an interactive manner, just by adding a switch to the command. The various switches you can use are the following:

        -v Verbose mode or this shows all the progress of the cp command as it is happening
        -i Interactive mode is the mode that will prompt you for confirmation on each command
        -R Recursive mode is the mode that will copy all the files and directories that are within that directory
        -f Force mode is the mode you want to force Linux to do the command regardless if this would copy over any other directory or file (use with caution)
        -p Preserve mode is the mode that will preserve the attributes of a file such as creation date and file permissions
        -u Update mode will only copy the file or folder if the source is newer than the destination
    
    Of course, you can add multiple switches to the cp command at once. As well, the -u update switch is very handy when creating a backup system in a script or some other ultility program.

For example if you wish to have the copy command in verbose mode you would use the following:

```
    cp -v [filename] [filenamecopy]
```

Or if you want to have the copy command in interactive mode you would do the following:

```
    cp -i [filename] [filenamecopy]
```
Or if you just want to force copy to copy the file and overwrite or basically ignore any warnings that may arise from copying a file.

```
    cp -f [filename] [filenamecopy]
```

As you can see the process is pretty much identical for all the other switches for this command so it would be pretty redundant to keep showing you examples of each and every switch.