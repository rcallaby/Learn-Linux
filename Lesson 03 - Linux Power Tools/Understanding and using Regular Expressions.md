# Understanding and using Regular Expressions

Regular expressions is probably one of the most useful things you can learn when learning Linux or computers in general. There are so many times when understanding Regular Expressions (RegEX) is handy. There are many programming languages that use it as part of its syntax. The number of times that I have used RegEx in every day life as a employee of a company is countless.

Understanding RegEx and using RegEx can be difficult. It is not easy by any means. Some still find it difficult after many years of using it. However, just because it is daunting doesn't make it any less useful. There are many online aids that can help you construct useful RegEx expressions. So, don't be intimidated by RegEx, rather just embrace it. The plus side of getting particularly good at RegEx is that you may be one of the most valuable members of your team at wherever you work.

Regular expressions (regex or regexp) are powerful tools for pattern matching and manipulation of text. They are widely used in Linux command-line utilities like grep, sed, and awk. This tutorial will guide you through the basics of regular expressions and provide examples of their usage in these utilities.

## Table of Contents:

Introduction to Regular Expressions
1.1 What are Regular Expressions?
1.2 Basic Concepts
Using Regular Expressions with grep
2.1 Searching with grep
2.2 Basic Patterns
2.3 Anchors and Boundaries
2.4 Character Classes
2.5 Quantifiers
Text Manipulation with sed
3.1 Find and Replace with sed
3.2 Addressing Lines
3.3 Basic sed Commands
3.4 Advanced Text Manipulation
Field Processing with awk
4.1 Introduction to awk
4.2 Basic Syntax
4.3 Using Regular Expressions in awk
4.4 Built-in Variables
Combining Commands
5.1 Piping and Chaining Commands
5.2 Examples of Combined Usage
Conclusion


### Introduction to Regular Expressions:
1.1 What are Regular Expressions?
Regular expressions are patterns that describe sets of strings. They provide a concise and flexible way to search for, match, and manipulate text based on specific patterns. In Linux, regular expressions are widely used in command-line utilities for searching and manipulating text.

1.2 Basic Concepts:

Literals: Characters that match themselves.
Metacharacters: Special characters with special meanings.
Anchors: Specify positions in a line, like the beginning (^) or end ($) of a line.
Character Classes: A set of characters enclosed in square brackets (e.g., [0-9]) to match any of the characters.
Quantifiers: Specify how many times a preceding element should occur (e.g., *, +, ?).
Groups and Alternation: Parentheses () to group elements and | for alternation.

### Using Regular Expressions with grep:
2.1 Searching with grep:
grep is a powerful command-line utility for searching text files using regular expressions. Syntax: grep [options] pattern [file]

2.2 Basic Patterns:

Search for a specific word: grep "pattern" file.txt
Case-insensitive search: grep -i "pattern" file.txt

2.3 Anchors and Boundaries:

Search at the beginning of a line: grep "^pattern" file.txt
Search at the end of a line: grep "pattern$" file.txt
Whole word search: grep -w "pattern" file.txt
2.4 Character Classes:

Match digits: grep "[0-9]" file.txt
Match any single character: grep "." file.txt
2.5 Quantifiers:

Match zero or more: grep "a*" file.txt
Match one or more: grep "a+" file.txt
Match zero or one: grep "a?" file.txt

### Text Manipulation with sed:
3.1 Find and Replace with sed:
sed is a stream editor that processes text line by line. It's often used for find-and-replace operations. Syntax: sed 's/pattern/replacement/' file.txt

3.2 Addressing Lines:

Apply to specific lines: 

```
sed '2,5s/pattern/replacement/' file.txt

```
3.3 Basic sed Commands:

Delete lines: 

```
sed '/pattern/d' file.txt

```
Print specific lines: 

```
sed -n '/pattern/p' file.txt
```
3.4 Advanced Text Manipulation:

Replace using captured groups: sed 's/\(old\)pattern/\1new/' file.txt
Append and insert lines: sed '/pattern/a new line' file.txt

### Field Processing with awk:
4.1 Introduction to awk:
awk is a versatile text processing tool that operates on fields (columns) of input. It's particularly useful for structured data.

4.2 Basic Syntax:

Print specific fields: 
```
awk '{print $1, $3}' file.txt

```

4.3 Using Regular Expressions in awk:

Match patterns and perform actions: awk '/pattern/ { action }' file.txt
4.4 Built-in Variables:

```
NR: Current record (line) number.
NF: Number of fields in the current line.
$0: The entire line.
$1, $2, etc.: Fields in the line.

```



### Combining Commands:

5.1 Piping and Chaining Commands:
You can pipe the output of one command to another using the | operator. For example: