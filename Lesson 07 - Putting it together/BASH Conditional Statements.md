# BASH Conditional Statements

Conditional statements are a crucial aspect of programming that allow developers to make decisions and execute specific blocks of code based on certain conditions. In the realm of shell scripting, BASH (Bourne Again SHell) provides a range of conditional statements that enable you to create powerful and flexible scripts. In this article, we will delve into BASH conditional statements, explore their various forms, and provide illustrative examples.

Why Conditional Statements?
Conditional statements are essential because they give your scripts the ability to respond intelligently to different situations. Whether you need to perform different actions based on user input, system states, or any other factors, conditional statements provide the mechanism to do so.

Basic Syntax
BASH conditional statements are often constructed using the if keyword, followed by a condition in square brackets ([ ]). The condition is evaluated, and if it is true, the corresponding block of code is executed. If the condition is false, the script moves on to the next set of instructions.

The basic syntax of an if statement looks like this:

```
if [ condition ]; then
    # Code to execute if the condition is true
fi

```

Comparison Operators
Comparison operators are fundamental for creating conditions in BASH. Here are some common comparison operators:
```
=: Equal to
!=: Not equal to
-eq: Equal (used for numeric comparisons)
-ne: Not equal (used for numeric comparisons)
-lt: Less than
-le: Less than or equal to
-gt: Greater than
-ge: Greater than or equal to

```
Logical Operators
Logical operators help combine multiple conditions to form more complex expressions. The main logical operators in BASH are:
```
&&: Logical AND
||: Logical OR
!: Logical NOT

```

BASH If Statements

Example 1: Checking for Equality

```
#!/bin/bash

user_input="apple"

if [ "$user_input" = "apple" ]; then
    echo "You entered 'apple'."
fi

```
Example 2: Numeric Comparison

```
#!/bin/bash

value=10

if [ "$value" -gt 5 ]; then
    echo "$value is greater than 5."
fi


```
Example 3: Using Logical AND

```
#!/bin/bash

age=18
has_license=true

if [ "$age" -ge 18 ] && [ "$has_license" = true ]; then
    echo "You are eligible to drive."
fi



```

Example 4: Using Logical OR

```
#!/bin/bash

is_weekend=false
is_holiday=true

if [ "$is_weekend" = true ] || [ "$is_holiday" = true ]; then
    echo "It's time to relax!"
fi

```

BASH If-Else Statements
Adding an else block allows you to provide an alternative set of instructions to execute when the condition is false.

Example 5: Using If-Else

```
#!/bin/bash

age=15

if [ "$age" -ge 18 ]; then
    echo "You are eligible to vote."
else
    echo "You are not eligible to vote yet."
fi


```

BASH If-Elif-Else Statements
When you have multiple conditions to check, you can use elif (short for "else if") statements.

Example 6: Using If-Elif-Else

```
#!/bin/bash

num=0

if [ "$num" -gt 0 ]; then
    echo "$num is positive."
elif [ "$num" -lt 0 ]; then
    echo "$num is negative."
else
    echo "$num is zero."
fi


```
Nested Conditional Statements
You can nest conditional statements to handle intricate decision-making scenarios.

Example 7: Nested If Statements

```
#!/bin/bash

num=12

if [ "$num" -gt 10 ]; then
    echo "$num is greater than 10."
    if [ "$num" -lt 20 ]; then
        echo "$num is also less than 20."
    fi
fi


```
BASH Case Statements
The case statement is useful when you have a variable and want to compare it against multiple possible values.

Example 8: Using Case Statements

```
#!/bin/bash

fruit="banana"

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
        echo "It's something else."
        ;;
esac


```

# Conclusion

Conditional statements in BASH provide the backbone for creating dynamic and responsive scripts. They empower you to build scripts that make decisions based on various conditions, user inputs, and system states. By mastering BASH conditional statements and their various forms, you can write more sophisticated and efficient shell scripts that cater to a wide range of scenarios. Through the examples provided in this article, you have gained valuable insights into creating effective BASH scripts with conditional statements. Now you're equipped to confidently incorporate these concepts into your own scripting endeavors.