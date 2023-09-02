# Reading a file line by line in BASH

With BASH you can read a file line by line, that is why you can use it to automate some mundane tasks. For instance, say you were told to set up a thousand new employee accounts. Doing this one by one would take hours and perhaps days.

However, you can set up a script in BASH that reads usernames to set up users with default settings just by reading in input from a file line by line. Of course, you do this by using a loop of some sort and obviously you would need to know exactly how you wish to have each user set up beforehand.

Or, say you want to add a set of users to the sudo group because they are being promoted. Again, you can just set up a script to add all users to that group or any other group you specify.

There are many other scenarios you can think of but that is just some of what you can do using this feature of being able to read a file line by line.

However, before we get into those complex scripts lets start with something simple. Here we have a script that reads a file line by line. It is really simple but starting with something simple is usually the best way to do things.
```
    while IFS= read -r line; do
	    printf ‘%s\n’ “$line”
    done < input_file
```
Now, you can add a conditional statement so that when you read input from the file it only prints out what you are desiring. For instance if you put in a if..then..else statement you can sort through the file to get only what you need so that you can just get the data you need.
