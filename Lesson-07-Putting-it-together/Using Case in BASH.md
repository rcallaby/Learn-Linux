# Using CASE in BASH

Step 1: Basic Syntax
The case statement has the following syntax:

```
case "$variable" in
    pattern1)
        # commands to execute if variable matches pattern1
        ;;
    pattern2)
        # commands to execute if variable matches pattern2
        ;;
    pattern3)
        # commands to execute if variable matches pattern3
        ;;
    *)
        # commands to execute for any other value of variable
        ;;
esac


```
Step 2: Using the case Statement

Start by setting up your Bash script and defining the variable you want to match patterns against.

```
#!/bin/bash

fruit="apple"


```

Use the case statement to match the value of the variable against different patterns. For each pattern, provide the corresponding commands to execute.

```
case "$fruit" in
    "apple")
        echo "It's an apple."
        ;;
    "banana")
        echo "It's a banana."
        ;;
    "orange")
        echo "It's an orange."
        ;;
    *)
        echo "It's an unknown fruit."
        ;;
esac

```

Step 3: Testing Different Cases
You can run your script and see the output for different values of the fruit variable.

```
$ ./fruits.sh
It's an apple.

$ ./fruits.sh
It's an unknown fruit.


```
Step 4: Using Wildcards
You can use wildcards to match multiple patterns. For instance, let's consider an example of categorizing animals based on their types:

```
#!/bin/bash

animal="dog"

case "$animal" in
    "cat" | "dog")
        echo "It's a pet."
        ;;
    "lion" | "tiger" | "bear")
        echo "It's a wild animal."
        ;;
    *)
        echo "It's an unknown animal."
        ;;
esac


```
Step 5: Numeric Ranges
You can also use numeric ranges with the case statement. For example, categorizing students based on their exam scores:

```
#!/bin/bash

score=85

case "$score" in
    0[0-4]|05)
        echo "Fail"
        ;;
    0[6-7][0-9]|080)
        echo "Pass"
        ;;
    09[0-9]|100)
        echo "Distinction"
        ;;
    *)
        echo "Invalid score"
        ;;
esac


```
Step 6: Using Variables in Patterns
You can use variables within patterns. Here's an example of categorizing fruits based on their color:

```
#!/bin/bash

fruit_color="yellow"

case "$fruit_color" in
    "red")
        echo "It's a red fruit."
        ;;
    "yellow" | "orange")
        echo "It's a citrus fruit."
        ;;
    "green")
        echo "It's an unripe fruit."
        ;;
    *)
        echo "Unknown fruit color."
        ;;
esac

```

Step 7: Handling User Input
The case statement is often used to process user input. Here's an example of a simple menu system:

```
#!/bin/bash

while true; do
    echo "Menu:"
    echo "1. Display date"
    echo "2. Display current directory"
    echo "3. Exit"
    read -p "Enter your choice: " choice

    case "$choice" in
        1)
            date
            ;;
        2)
            pwd
            ;;
        3)
            echo "Exiting."
            exit 0
            ;;
        *)
            echo "Invalid choice."
            ;;
    esac
done


```

The case statement in Bash provides a flexible and readable way to handle multiple conditional branches. By following this tutorial and exploring the examples provided, you can become proficient in using the case statement to streamline your scripting tasks.