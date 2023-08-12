# Using alias in Linux

The alias command in Linux allows you to create a shortcut for a different command. Or alternatively, if you know you misspell or mistype a command regularly the alias command allows you to correct that mistake by default. Some people do this on a regular basis. The whole point of Linux is to make your life easier, that is why there is an alias command. 

You probably aren't even aware of it but you may have already been using alias as it is defined for you in the bashrc file of your system. You can set alias commands from the command line but the true power is when you incorporte them into a bashrc file for later use. The best way to check to see if an alias command works is by first trying it out on the command line before placing it in the bashrc file. That is what this tutorial is going to cover.

The alias command is very similar to setting environmental variables in that the syntax is quite similar. For instance in order to create an alias that uses a term search in place of grep you would use the following:

```
    alias search=grep
```

So instead of using grep you would type search to find a particular bit of text in your system.

Or alternatively, it is very common to subsitute many of the ls variations as an alias for example:

```
    alias l='ls -al'
```
Typing one letter l is significantly better than typing four such as ls -al

As you can see using the alias command is pretty easy. You just start by using alias followed by the command you wish to use then the equals sign and then the longer version of what you want it to be subsituted for.

You can do this for a variety of items in your Linux operating system. For many, using alias is a bit personal and you may want to figure out your own shortcuts to various Linux commands you use frequently.

You can also use alias to make sure you don't make a mistake. For instance, it is very easy to screw things up in Linux by using the mv command or the move command so you could set up an alias so that it always defaults to the interactive mode to prevent you from making a mistake.

```
    alias mv='mv -1'
```

Of course, every alias you create on the command line is only present during your logged in session. That means you need a way to make these more permanenet and as I mentioned above the best way to do that is through a bashrc file.

One caveat is that when using a bashrc file you assume you use BASH as your default shell. There are different rc or resource files for various shells. However,that is outside of the scope of this course. Feel free to research those on your own.

