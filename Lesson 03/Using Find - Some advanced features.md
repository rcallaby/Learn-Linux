<strong>Using Find – Some of the more advanced features</strong>

Find can be pretty handy, and you can use it to execute commands such as finding all the empty files in a directory and deleting them. Alternatively, you can find all of the empty directories in a subdirectory and delete them.

You can also use find to find all of the files of a specific type and then change their permissions to a different type. This can be very useful if you wish to modify or change files and directories in bulk.

However, it would be best if you were careful when executing such commands as doing so on the wrong directory or the wrong files could cause serious harm to your operating system. So, use these commands with caution.

You can find files that have been modified in the past hour using an example like this:
```
    find . -mmin -60
```
You can find files with a range of sizes such as between 1 and 10 MB
```
    find / -size +1M -size -10M
```
Alternatively, you can find files of a greater size:
```
    find . -size +2M
```
Or you can execute a command by a certain filter such as a PHP extension:
```
    find /Documents -name “*.php” -exec rm{} \;
```
As you can see, the find command is very versatile, and you can use it quite easily with practice. You can use this command to your advantage.
