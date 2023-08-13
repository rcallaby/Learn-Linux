# Safely Shutdown Linux

Linux just like any other operating system has various methods to safely shutdown or reboot the system. Knowing how to do this from the command line is helpful for a variety of reasons. For instance, when backing up your system you may want to shutdown for the rest of the day if the backup was successful. If the backup failed you may want to just reboot the system.

Sometimes, when shutting down Linux you may encounter an error where the ending screen falters. If this should happen it is most like a video driver conflict that is causing the issue. Or some other hardware driver conflict that causes the issue. It is sometimes difficult to really diagnose the root issue. Looking at the logs in your Linux system may be helpful though.

That being said there are advantages of knowing and understanding how to shutdown your system using a variety of methods.

The shutdown command is what causes your Linux OS to terminate all processes in a organized fashion and eventually shuts down the system entirely. You can just type this command in by itself with no switches or other attributes and within 60 seconds your system will be shutdown.

You can use the command as the following:

```
    sudo shutdown
```
If you would like to terminate Linux at a specific time you can specifiy that time by adding it to the command in the following manner:
```
   sudo shutdown 22:00
```
The above command would shutdown the system at 22:00. The reason why this is particularly helpful is for instances you are using a virtual machine on a cloud provider that charges you per minute a computer is left on. If you know you may forget to turn off your virtual machine when you quit for the day then typing this command in could save you lots of money as you don't want to spend for a idle computer that you are not actively using.

You can also shutdown your system immediately by using the following command:

```
   sudo shutdown now
```
Now, if this Linux computer is on a network and is acting like a server you may want to send a message to all machines on the network. This can be accomplished by using the following command:

```
    sudo shutdown 22:00 "The server will be shutdown at 22:00 please save all work before this happens"
```

Now, as I mentioned above there are various ways that Linux can be shutdown. 

For instance if you want to power off Linux you can use the following command:

```
    sudo shutdown -h +10 "The system will be powered off in ten minutes, please save your work"
```
What the above command demonstrates is another way to shutdown Linux in a delayed fashion. By adding the -h switch and the +10 switch you speificy the manner and time whne Linux will shutdown. As well, a message will be broadcast to all computers on the network.

To cancel the shutdown command you would simply use the following:

```
    sudo shutdown -c
```

I would encourage you to look up the shutdown command using your systems man pages. From there you can get a lot more information on how this seemingly simple command can be used.