<strong>Changing Ownership of Files and Folders</strong>

A file or folder has many attributes. Not only does the file or folder have a set of permissions it also has an assigned ownership. This ownership can be assigned to an individual person or a group. Having this level of granuality helps to make Linux very secure against hackers as well as those who may want to explore files they shouldn't in your network.

As a Linux user it is important to know how to change the ownership of files and folders on your system. To do so you can use the chown command, which stands for change ownership as you can imagine.

You will most likely need to have sudo or root privileges in order to use this command.

To use the chown command is very simple for example:

```
    sudo chown accounting ./accounts/
```

This command assigns the accounting group to the ./accounts folder. You can check this by using the following:

```
    ls -l -d ./accounts/
```

Now, this is assuming you have both a accounting group and a ./accounts folder on your system. If you don't you could just create them to simulate exactly what I have done above. Or if you are very smart you could create a group and a folder of your own as assign ownership to that new folder.

You can use the chown command to assign the ownership of a specific file as well as a folder. For instance:

```
    sudo chown accounting payables-procedures.txt
```
This would assign the accounting group to the text file payables-procedures.txt.

You can use the exact same command to assign a user to a specific folder or a specific file by using the exact same command but instead of where the group name is you would use a username instead.

As you can see the chown command can come in quite handy if you want to restict access to a specific file or folders on your network. I would encourage you to look at the man pages for chown to explore all the possibilities of this command.