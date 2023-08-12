# Change the default shell

The shell of Linux is typically, for the most part, BASH or as many call it the BASH shell. This is what most of this course covers. However, during updates of some packages you may notice that your shell may be changed. This is because some packages were tested in different shells and the creator of those packages may have felt it necessary to change your default shell without your knowledge.

Changing a default shell is fairly straightforward, and you may want to do it to explore the alternatives to BASH that are out there. Checking to see what shell you are using is a simple command. And changing your default shell back to BASH is also very straightforward. Below I will show you how to do both.

To find what available shells you have on your system you could use the following command:
```
    cat /etc/shells
```
This lists all the available shells in the /etc/shells directory in your system. The command cat essentially just prints out to the screen the contents of what is in /etc/shells. I cover the cat command in a different part of this course.

To find out what is your current shell you would simply use the following:

```
    ps -p $$
```
To change your shell you would use the following command chsh which as you can imagine stands for change shell. It is used in the following manner:

```
    chsh -s /bin/bash
```
This would change what ever you are using to the BASH shell. Of course, depending upon what shells you have on your system you could change it to something completely different. As an example:

```
    chsh -s /bin/zsh
```
This changes the shell from whatever you are using to the zsh shell.

Different Linux shells have their advantages and their drawbacks. For instance some shells treat how they record the history of commands used differently.

As you grow as a Linux user I would encourage you to explore different shells that you can use on your system. Figure out which may be best for you to use. However, the scope of this course covers primarily the BASH shell, so don't expect support from me if you choose to change your shell on your system to something different than the BASH shell.

