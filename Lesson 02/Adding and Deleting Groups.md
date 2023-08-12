<strong>Adding and Removing groups to Linux</strong>

You may want to add groups for a variety of reasons

Groups allow you to categorize and organize people and files
Given how the Linux file permissions are set up adding a group for those permissions is helpful

To add a group you would use the command groupadd
So the command would be the following
```
    sudo groupadd <groupname>
```
If there is already a group of that name you would get an error message.

As well, there is no difference between a standard user group and a system group. However, some people create a system group in order to perform system tasks such as routine backups of the system.

You can specify a password for a group however if more than one person or member is a part of that group then you may get an error message

You can remove a group by typing the command groupdel and then the group name
For instance you would type
```
    groupdel <groupname> 
```
to delete a group from the system.

If the group no longer exists and you try and remove it you will get an error message
Okay, now that you have created a new group you would want to add users to that group so that you can administer them appropriately.

To add a user to a group you can use the usermod command.

For instance to add a user to a group you would use the following command:
```
   sudo usermod -a -G sudo Richard
```
This adds the user Richard to the sudo group.

If you want to add Richard to the sudo group so that it is the primary group you would use the following:
```
    sudo usermod -g sudo Richard
```
