<strong>Adding and Deleting Users to Linux</strong>

It would make sense that if you were learning how to use Linux you would want to know how to add users to your operating system.
Most people share a computer, whether you have a family, business, or whatever sharing a computer usually involves multiple user accounts.

As Linux was based upon Unix adding users is fairly painless.

There are both graphical user interface ways to add users as well as the most preferred way which is through the command line.
The reason why you want to learn how to master the command line on Linux is not only does it give you more power but it is also more likely that you will be a job candidate if you know how to properly use and operate Linux from the command line. That is why I show you both ways but I am going to be honest I think the command line is the best way to go.

<b>Adding users</b>

To add a user to Linux you would need to type the following:
```
    sudo useradd Bob -m 
```

This would create a new user Bob with a home directory

Now you would want to specify a default shell
So if you wanted to define a default shell you would instead type the following
```
    sudo useradd Bob -m -s /bin/bash
```
So we created a new user but it doesn’t have a default group, we should really do that at the first step
So you would add the following to the line
```
    sudo useradd Bob -m -s /bin/bash -g users
```

This will create the user Bob and create the home directory as well as define the default shell and assign the new user to the users group

Alternatively you can specify any additional groups to the command by typing a capital G following the lower case g such as the following
```
    sudo useradd Bob -m -s /bin/bash -g users -G sudo
```

So, after we created the user you will then need to set a password for the user

To set a different password for another user you would type the following:
```
    sudo passwd Bob
```

And then you would follow the prompts to set a new password

<b>Deleting users</b>

To delete a user you must have sudo access so don’t try to do this if you don’t you would just get an error message.
By default you should create a user without sudo privileges that you will use on a day to day basis. You don’t want to continuously use Linux as admin as that is a security risk

To delete a user you would simply just type the following:
```
    sudo deluser <username>
```

Now this will delete the user but keep their home directory and all of the files
If you want to remove everything you should type the following:
```
    sudo deluser -r <username>
```