<strong>Using Find is the most powerful commands</strong>

Find is both extremely simple to use and also extremely powerful at the same time.

Find files in the current directory
```
    find . -name <filename>
```
Find files regardless of capitalialism
```
    find . -iname <filename>
```

Find files in a certain directory
```
    find /home -name <filename>
```

Find files in a certain directory regardless of case
```
    find /home -iname <filename>
```

Find all files of php type in the current directory
```
    find . -type f -name “*.php”
```

Find all files with 777 Permissions
```
    find . -type f -perm 0777
```

Find all read only files in a current directory
```
    find / -perm /u=r
```

Find all executable files
```
    find / -perm /a=x
```

Find all empty files
```
    find /tmp -type f -empty
```

Find all empty directories
```
    find /tmp -type d -empty
```

Find all hidden files
```
    find /tmp -type f -name “.*
```

Find all files based on user
```
    find /home -user Bob
```

Find all files based upon group
```
    find /home -group users
```

