# Bash Conditional Operators

- Introduction to Conditional Operators
- Basic Comparison Operators
- Logical Operators
- Compound Conditions
- Case Statements
- Short-Circuiting
- Nested Conditionals
- Exit Status and Conditional Execution
- Conclusion


## Introduction to Conditional Operators

Conditional operators in bash allow you to create decision-making structures within your scripts. These structures help control the execution of commands based on whether certain conditions are met. There are various types of conditional operators in bash, including comparison operators, logical operators, and special constructs like case statements.

## Below is a listing of the conditional operators in BASH 

- eq = returns true if two numbers are equilivent
- lt = returns true if one number is less than the other
- gt = returns true if one number is greater than the other
- == - means this will return true if two strings are equal to each other
- != returns true if two strings are not equal
- ! – returns true if the expression is false
- -d  checks the existence of a directory
- -e checks the existence of a file
- -r checks the existence of a file and read permission
- -w checks the existence of a file and write permission
- -x checks the existence of a file and execute permission

Basic Comparison Operators

Comparison operators are used to compare values and determine whether a condition is true or false. Here are some of the most commonly used comparison operators:

- -eq: Equal to
- -ne: Not equal to
- -lt: Less than
- -le: Less than or equal to
- -gt: Greater than
- -ge: Greater than or equal to

```
#!/bin/bash
a=10
b=20

if [ $a -eq $b ]; then
    echo "a is equal to b"
else
    echo "a is not equal to b"
fi

```

## Logical Operators

Logical operators allow you to combine multiple conditions and create more complex decision-making structures. The common logical operators in bash are:

- &&: Logical AND
- ||: Logical OR
- !: Logical NOT

```
#!/bin/bash
age=25

if [ $age -gt 18 ] && [ $age -lt 30 ]; then
    echo "You are between 18 and 30 years old."
else
    echo "You are not in the specified age range."
fi

```
## Compound Conditions

You can combine comparison operators and logical operators to create compound conditions. Parentheses are used to control the order of evaluation.

```
#!/bin/bash
x=5
y=10

if [ $x -gt 0 ] && [ $y -lt 20 ]; then
    echo "Both conditions are true."
else
    echo "At least one condition is false."
fi

```

## Case Statements

Case statements offer a convenient way to handle multiple possible values of a variable or expression. They are especially useful when dealing with a large number of options.

```
#!/bin/bash
fruit="apple"

case $fruit in
    "apple")
        echo "It's an apple."
        ;;
    "banana")
        echo "It's a banana."
        ;;
    *)
        echo "It's neither an apple nor a banana."
        ;;
esac

```
## Short-Circuiting

Bash employs short-circuiting in logical operations. This means that if the result of a logical operation can be determined from the first condition, the second condition is not evaluated.

```
#!/bin/bash
x=5

if [ $x -eq 5 ] || [ $((x/0)) -eq 0 ]; then
    echo "Logical OR short-circuiting."
else
    echo "This won't be printed."
fi


```
## Nested Conditionals

You can nest conditional statements within each other to create more intricate decision structures.

```
#!/bin/bash
age=22

if [ $age -gt 18 ]; then
    if [ $age -lt 25 ]; then
        echo "You are an adult under 25."
    else
        echo "You are an adult over 25."
    fi
else
    echo "You are not an adult."
fi


```

## Exit Status and Conditional Execution

Every command in bash returns an exit status, where 0 usually indicates success and non-zero values indicate errors. Conditional execution of commands can be achieved using && and || operators.

```
#!/bin/bash
mkdir my_directory && echo "Directory created." || echo "Failed to create directory."

```
# Conclusion

Conditional operators are an integral part of bash scripting, enabling you to create dynamic and responsive scripts. By mastering these operators, you can craft powerful scripts that adapt to different scenarios and conditions. With comparison operators, logical operators, case statements, and other constructs at your disposal, you have the tools you need to create versatile and efficient bash scripts.

Remember, practice is key to becoming proficient in using conditional operators. Experiment with different combinations, explore real-world scenarios, and enhance your scripting skills.
