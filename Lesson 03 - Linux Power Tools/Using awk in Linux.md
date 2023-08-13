# Using awk in Linux

AWK is a powerful text processing tool commonly used in Unix-like operating systems, including Linux. It's particularly useful for working with structured text data, such as CSV files or log files. Here's a step-by-step tutorial with various examples to help you get started with AWK:

### Step 1: Basic Syntax
AWK programs consist of patterns and actions. An action is enclosed in curly braces {}, and a pattern specifies when the action should be executed. If no pattern is specified, the action is executed for every input line.

### Step 2: Running AWK
You can run AWK directly from the terminal. The basic syntax is:

```
awk 'pattern { action }' input_file

```
### Step 3: Printing Columns
Let's start with a simple example of printing columns from a file. Suppose you have a file named "data.txt" containing the following content:

```
Alice 25
Bob 30
Charlie 28

```
You can print the first column (names) using the following command:

```
awk '{ print $1 }' data.txt

```

### Step 4: Using Delimiters
AWK treats whitespace as the default delimiter. To work with other delimiters, use the -F option. For example, using a colon (:) as a delimiter:

```
awk -F':' '{ print $1 }' data.txt

```
### Step 5: Using Patterns
Patterns determine when the associated action should be executed. For example, let's print only the lines where the age is greater than 27:

```
awk '$2 > 27 { print }' data.txt

```

### Step 6: Combining Patterns and Actions
You can use multiple patterns and actions in an AWK program. For instance, print the names of people whose age is greater than 27:

```
awk '$2 > 27 { print $1 }' data.txt

```
### Step 7: Using Built-in Variables
AWK provides many built-in variables. Some common ones include:

- $0: The entire input line.
- $NF: The number of fields in the current line.
- NR: The current record (line) number.
- FS: The field separator.

### Step 8: Calculations
You can perform calculations using AWK. Calculate and print the average age:

```
awk '{ sum += $2 } END { print "Average age:", sum/NR }' data.txt

```
### Step 9: Conditional Statements
AWK supports if-else statements. Print "Adult" if age is greater than 18, otherwise print "Minor":

```
awk '{ if ($2 > 18) print $1, "Adult"; else print $1, "Minor" }' data.txt

```
### Step 10: Regular Expressions
AWK can use regular expressions for pattern matching. Print lines where names start with "A":

```
awk '$1 ~ /^A/ { print }' data.txt

```
### Step 11: Redirecting Output
You can redirect AWK's output to a new file:

```
awk '{ print $1 }' data.txt > names.txt

```

These examples cover the basics of using AWK in Linux. AWK is a versatile tool that can be used for various text manipulation tasks. Experiment with different examples to become more comfortable with its capabilities.