<strong>Using the chage command</strong>

The people who use your network are by far the biggest points of failure in any network security plan. This is why you should encourage frequent password changes. The industry standard is 90 days but if you are working on something very sensitive then you may want to change that to something even more extreme such as 45 days. As well, if you believe you have been compromised you can force a password change on all of the users on the network using the chage command.

Now, later on I discuss how to create BASH scripts. Of course, the best way to manage potentially thousands of users is to create a BASH script that automatically performs a task such as this, doing otherwise would be very time consuming and a waste of effort. Whenever you can write a script to make your job easier, you should.

That being said you should be able to learn how to manage users by using the following example commands.

To audit a user you would use the following command:
```
    chage -l [username]
```
This shows or rather lists all of the attributes of a particular user on the system. It shows the time the last password was changed, how long until the password expires, if the account ever expires and the min and max days until a password change.

In order to change some of these attributes you could use one of the following commands:
```
    chage -m 1 -M 90 [username]
```

What this does is changes the password expiration to 90 days with the minimum number of days between password changes to only 1 day. Of course, I would also recommend you make sure to give enough warning to your users that a password change is coming up. The typical amount of time to warn users is 7 days. This can also be set using the chage command.

I would highly recommend you look into the man page of the chage command to see what else you can do with this, as if you ever do become a network administrator you may have to use this particular command on a regular basis.

