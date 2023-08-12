<strong>Changing Permissions and Ownership of Files and Folders</strong>

There are two commands in linux to change permissions and ownership of a file or directory.

You would want to change ownership depending upon who created the file first. For instance, if Bob originally created the file he would have ownership and permissions for that file. But if a user named Sally wanted to take over the file for some reason she would need to own it and have full permissions.

<b>The chown command</b>

The command to change ownership is chown which as you can imagine stands for change ownership

<b>The chmod command</b>

The command to change permissions is chmod which changes permissions for the file.

An example command would be the following:
```
    sudo chmod -R ugo+rw ~/Documents/sourcecode
```
This means that all the users, groups, and every body else would have full read write permissions for the source code folder in Documents and all of the subfolders

Conversely you can change the ownership of the whole directory to be of another user such as user Richard
```
    sudo chown -R ~/Documents/Templates
```
This would change all of the ownership of the templates subfolder to the Richard user.

