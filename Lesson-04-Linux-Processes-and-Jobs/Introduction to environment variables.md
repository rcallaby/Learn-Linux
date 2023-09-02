<strong>Environment Variables in Linux</strong>

So, we discussed how to set the default bash shell. This setting is known as a environment variable. It turns out you can set or change a variety of environment variables at any time. The listing of environment variables is quite large but you can set such things as:

pwd - Present working directory
logname – The name of the user
hostname – which is the name of the computer on the network
editor – the devices default editor

You can use the printenv command to print all of the environment variables that are available.
To set an environment variable you would just set it using the following:
    variablename = variable_value

For instance say you wanted to change the hostname of your computer you would set it using the following:
```
    hostname=newhostname
```

To confirm that a value has been set you can use the following:
```
    set | grep [variablename]
```

All of these variables only last as long as your log in your session is current. Or rather to say it better as long as you are using the computer these variables will hold true, but once you turn off the computer these variables will change unless you use some other method to set the environment variables.

These environment variables are set in the .bashrc file located in your home directory. Each .bashrc file is local so keep that in mind. Each user can set their own environment variables.


