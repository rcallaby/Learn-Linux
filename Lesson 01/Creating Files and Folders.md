<strong>Creating Files and Directories in Linux</strong>

To create a file you can use the command touch such as the following:
```
    touch <filename>
```
You can of course add an extension to the file such as html, xml, or what ever you wish

Files in Linux do not need an extension to determine their type. However, adding an extension can help with whatever program you’re using to open the file and determine its use.

For instance, many code editors use file extensions to determine what debuggers or linters to use with the file. Or some word processors use file extensions to determine what to do with the file.

You can also make directories in linux with the mkdir command
An example of this would be the following:
```
    mkdir <directoryname>
```

The mkdir command will create what ever directory name you specify in what ever director you are in but you aren't limited to this in Linux.

You can also make a directory outside of the relative path by specifying a specific path

As well you can add permissions to the directory by using the -m option followed by the permission level
For instance, you can use the follwoing:
```
    mkdir -m777 /Documents/Sue 
```
That will apply the 777 level of permissions to the directory /Documents/Sue

You can add parent directories to your current directory by applying the -p switch the -p switch applies the parent switch to the directory

As well, you can add multiple directories at a time by simply listing them or by placing them in a {} curly braces with commas

As you can see the mkdir command is quite versatile and very handy if you wish to properly organize your file system. Using this knowledge you should be able to stay organized and keep things organized so that you can reference your files at a later date.
