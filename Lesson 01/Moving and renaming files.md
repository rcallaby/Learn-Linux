<strong>Moving and renaming files and folders in Linux</strong>

To move and rename files you can use the same command.

The mv command can be used for both functions.

That makes it <b>really</b> convenient.

You can move one directory by specifying its path and then a different path you wish the directory to be moved to.

You may have to create the directory ahead of time before you move it into the new location. Otherwise you would get an error.
To rename a directory you would just simply type the directory name and the name you wish to rename it on the same line and that moves all files and subfolders and then renames the directory.

The same procedure is done with renaming files. You just simply type mv and then the file name and the file name you wish it to be renamed. It really is that simple.

For instance you would use the following command to rename a file:
```
    mv [filename] [newfilename]
```

You can force prompts before a file is overwritten by specifying the -i switch
If you rename a file that already has that name it will be overwritten

For instance:
```
    mv -i [filename] [new location of filename]
```

Alternatively if you wish to force the overwriting procedure you can simply type the -f which forces the operation without any prompts or warnings.
An example of this would be:
```
    mv -f [filename] [newfilename or location]
```

As well you can specifiy the -n switch which will never overwrite the file, if the filename already exists then nothing will happen.
```
    mv -n [filename] [newfilename]
```

The -b switch allows you to create a backup of the original file. The backup file will have the ~ appended to it.
Finally the -v switch is for verbose output and that tells you exactly what is going on with this operation.

An example of this would be the following:
```
    mv -b [filename]
```
This would produce a filename such as the following:
```
    [filename~]
```

As you can see the mv command is pretty powerful. That is true with many Linux commands. The more powerful commands tend to look very simple but have many different avenues or ways that you can use them. Of course, I would encourage you to look into all the ways you can use this command and any other commands that you may use on a day to day basis.