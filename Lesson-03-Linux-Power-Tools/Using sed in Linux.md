# Using sed in Linux

### Step 1: Basic Syntax
The basic syntax of the sed command is as follows:

```
sed [options] 'commands' input-file(s)

```
options: Various options to modify the behavior of sed. Common options include -i (in-place editing), -n (suppress automatic printing), etc.
'commands': A series of editing commands enclosed in single quotes.
input-file(s): The file(s) on which you want to perform text manipulation.

### Step 2: Common Commands

Example 1: Print Lines
To print lines from a file, use the p command.

```
sed -n 'p' file.txt   # Print all lines from file.txt

```
Example 2: Replace Text
To replace text, use the s command.

```
sed 's/old/new/' file.txt         # Replace the first occurrence of 'old' with 'new' in each line
sed 's/old/new/g' file.txt        # Replace all occurrences of 'old' with 'new' in each line
sed 's@/path/to/old@/new@' file.txt  # Use different delimiter (@) for better readability

```
Example 3: Delete Lines
To delete lines, use the d command.

```
sed '/pattern/d' file.txt   # Delete lines containing 'pattern'
sed '1,5d' file.txt         # Delete lines 1 to 5

```
### Step 3: Using Regular Expressions
sed supports regular expressions for more advanced text manipulation.

Example 5: Match Lines
To match specific lines using regular expressions:

```
sed -n '/pattern/p' file.txt   # Print lines containing 'pattern'

```
Example 6: Using Capture Groups
You can use capture groups in the replacement text:

```
sed 's/\(start\)\(.*\)\(end\)/\3\2\1/' file.txt  # Reorder 'start', 'middle', 'end' to 'end', 'middle', 'start'

```
### Step 4: In-Place Editing
sed can modify files in-place using the -i option.

Example 7: In-Place Editing

```
sed -i 's/old/new/' file.txt   # Replace 'old' with 'new' in file.txt (modifies the file)

```
### Step 5: Combining Commands
You can combine multiple commands using semicolons.

Example 8: Combining Commands

```
sed -e 's/foo/bar/; s/baz/qux/' file.txt   # Replace 'foo' with 'bar' and 'baz' with 'qux'

```
### Step 6: Using Variables
You can use variables to make your sed commands more flexible.

Example 9: Using Variables

```
pattern="search-pattern"
replacement="new-text"
sed "s/$pattern/$replacement/" file.txt    # Use variables in the sed command

```
### Step 7: Working with Ranges
sed allows you to specify ranges of lines.

Example 10: Range of Lines

```
sed '10,20s/old/new/' file.txt   # Replace 'old' with 'new' in lines 10 to 20


```
### Step 8: Deleting Empty Lines
You can use sed to delete empty lines.

Example 11: Delete Empty Lines

```
sed '/^$/d' file.txt   # Delete all empty lines from file.txt

```
# Conclusion
These examples cover a wide range of common sed operations. Remember that sed can be quite complex, and this tutorial only scratches the surface. For more advanced operations and techniques, you might want to consult the official sed documentation or further resources.