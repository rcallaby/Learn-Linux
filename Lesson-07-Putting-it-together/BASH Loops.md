# BASH Loops

Bash loops are essential constructs that allow you to repeatedly execute a series of commands based on a condition. There are mainly two types of loops in Bash: for loops and while loops. Let's dive into a detailed step-by-step tutorial for both types, using various examples.


for Loop:
Step 1: Basic Syntax

The basic syntax of a for loop in Bash is as follows:

```bash
for variable in list
do
    # commands to be executed for each iteration
done


```
Step 2: Example - Iterating through Numbers

```bash
for num in 1 2 3 4 5
do
    echo "Number: $num"
done


```

Step 3: Example - Iterating through Files

```bash
for file in *.txt
do
    echo "Processing file: $file"
done


```
Step 4: Example - Generating a Sequence

```bash
for ((i=1; i<=5; i++))
do
    echo "Value: $i"
done


```
Step 5: Iterating over Command Output

```bash
for user in $(cat users.txt)
do
    echo "Hello, $user!"
done


```
while Loop:

Step 1: Basic Syntax

The basic syntax of a while loop in Bash is as follows:

```bash
while [ condition ]
do
    # commands to be executed as long as condition is true
done


```
Step 2: Example - Counting Down

```bash
count=5
while [ $count -gt 0 ]
do
    echo "Countdown: $count"
    ((count--))
done


```
Step 3: Example - Reading User Input

```bash
input=""
while [ "$input" != "quit" ]
do
    echo "Enter 'quit' to exit: "
    read input
done


```
Step 4: Example - Running Until a Condition is Met

```bash
random_num=$((RANDOM % 10))
while [ $random_num -ne 5 ]
do
    echo "Random number is not 5. Trying again..."
    random_num=$((RANDOM % 10))
done
echo "Found 5!"


```
Step 5: Example - Reading Lines from a File

```bash
while IFS= read -r line
do
    echo "Line: $line"
done < data.txt


```
These examples should provide you with a solid foundation for using for and while loops in Bash. Remember to adjust the conditions, commands, and variables according to your specific needs. Loops are powerful tools for automating repetitive tasks and handling dynamic situations.
