# Shell Scripting

## What is Shell Scripting?

A shell script is a file containing a series of Linux commands that are executed by a shell interpreter.

Instead of typing commands manually, you can automate tasks using scripts.

### Benefits of Shell Scripting

* Automation of repetitive tasks
* System administration
* Log analysis
* Backup management
* Deployment automation
* Task scheduling

---

# What is a Shell?

A shell is a command-line interpreter that executes commands entered by the user.

Common shells:

| Shell | Description                |
| ----- | -------------------------- |
| sh    | Bourne Shell               |
| bash  | Bourne Again Shell         |
| zsh   | Z Shell                    |
| fish  | Friendly Interactive Shell |
| ksh   | Korn Shell                 |

Check current shell:

```bash
echo $SHELL
```

Example output:

```text
/bin/bash
```

---

# Creating Your First Script

Create a file:

```bash
touch hello.sh
```

Open and edit:

```bash
nano hello.sh
```

Add:

```bash
#!/bin/bash

echo "Hello World"
```

Save and exit.

---

# Making Script Executable

Grant execute permission:

```bash
chmod +x hello.sh
```

Run script:

```bash
./hello.sh
```

Output:

```text
Hello World
```

---

# Shebang

The first line of a script is called the shebang.

```bash
#!/bin/bash
```

It tells Linux which interpreter should execute the script.

Examples:

```bash
#!/bin/bash
#!/bin/sh
#!/usr/bin/env bash
```

Recommended:

```bash
#!/usr/bin/env bash
```

---

# Comments

Single-line comments:

```bash
# This is a comment
echo "Hello"
```

Multiple comments:

```bash
# Author: John
# Version: 1.0
# Purpose: Demo Script
```

---

# Variables

## Creating Variables

```bash
name="Linux"
version="Ubuntu"
```

Access variables:

```bash
echo $name
echo $version
```

Or:

```bash
echo "${name}"
```

Output:

```text
Linux
Ubuntu
```

---

# User Input

Read user input:

```bash
#!/bin/bash

echo "Enter your name:"
read name

echo "Welcome $name"
```

Example:

```text
Enter your name:
John
Welcome John
```

---

# Command Line Arguments

Script:

```bash
#!/bin/bash

echo "First Argument: $1"
echo "Second Argument: $2"
```

Run:

```bash
./script.sh Linux Bash
```

Output:

```text
First Argument: Linux
Second Argument: Bash
```

---

# Special Variables

| Variable | Description         |
| -------- | ------------------- |
| $0       | Script name         |
| $1-$9    | Arguments           |
| $#       | Number of arguments |
| $@       | All arguments       |
| $?       | Exit status         |
| $$       | Process ID          |

Example:

```bash
echo "Script Name: $0"
echo "Arguments Count: $#"
```

---

# Output Commands

## echo

```bash
echo "Hello World"
```

---

## printf

```bash
printf "Name: %s\n" "Linux"
```

Output:

```text
Name: Linux
```

---

# Arithmetic Operations

Using double parentheses:

```bash
a=10
b=5

result=$((a+b))

echo $result
```

Output:

```text
15
```

Examples:

```bash
echo $((10+5))
echo $((10-5))
echo $((10*5))
echo $((10/5))
echo $((10%3))
```

---

# Conditional Statements

## if Statement

```bash
if [ 5 -gt 3 ]
then
    echo "True"
fi
```

---

## if-else

```bash
age=18

if [ $age -ge 18 ]
then
    echo "Adult"
else
    echo "Minor"
fi
```

---

## if-elif-else

```bash
marks=85

if [ $marks -ge 90 ]
then
    echo "Grade A"
elif [ $marks -ge 75 ]
then
    echo "Grade B"
else
    echo "Grade C"
fi
```

---

# Comparison Operators

## Numeric Operators

| Operator | Meaning               |
| -------- | --------------------- |
| -eq      | Equal                 |
| -ne      | Not Equal             |
| -gt      | Greater Than          |
| -lt      | Less Than             |
| -ge      | Greater Than or Equal |
| -le      | Less Than or Equal    |

Example:

```bash
if [ $a -gt $b ]
then
    echo "A is larger"
fi
```

---

## String Operators

| Operator | Meaning      |
| -------- | ------------ |
| =        | Equal        |
| !=       | Not Equal    |
| -z       | Empty String |
| -n       | Not Empty    |

Example:

```bash
if [ "$name" = "Linux" ]
then
    echo "Match"
fi
```

---

# Case Statement

Alternative to multiple if-else blocks.

```bash
read option

case $option in
    start)
        echo "Starting..."
        ;;
    stop)
        echo "Stopping..."
        ;;
    restart)
        echo "Restarting..."
        ;;
    *)
        echo "Invalid Option"
        ;;
esac
```

---

# Loops

## For Loop

```bash
for i in 1 2 3 4 5
do
    echo $i
done
```

Output:

```text
1
2
3
4
5
```

---

## Range Loop

```bash
for i in {1..10}
do
    echo $i
done
```

---

## While Loop

```bash
count=1

while [ $count -le 5 ]
do
    echo $count
    ((count++))
done
```

---

## Until Loop

Runs until condition becomes true.

```bash
count=1

until [ $count -gt 5 ]
do
    echo $count
    ((count++))
done
```

---

# Break and Continue

## break

```bash
for i in {1..10}
do
    if [ $i -eq 5 ]
    then
        break
    fi

    echo $i
done
```

---

## continue

```bash
for i in {1..10}
do
    if [ $i -eq 5 ]
    then
        continue
    fi

    echo $i
done
```

---

# Functions

Define function:

```bash
greet() {
    echo "Welcome"
}
```

Call function:

```bash
greet
```

---

## Function with Arguments

```bash
greet() {
    echo "Hello $1"
}

greet Linux
```

Output:

```text
Hello Linux
```

---

# Arrays

Create array:

```bash
fruits=("apple" "banana" "mango")
```

Access element:

```bash
echo ${fruits[0]}
```

Output:

```text
apple
```

All elements:

```bash
echo ${fruits[@]}
```

Array length:

```bash
echo ${#fruits[@]}
```

---

# Reading Files

Example file:

```text
apple
banana
mango
```

Script:

```bash
while read line
do
    echo $line
done < fruits.txt
```

---

# File Tests

| Test | Description      |
| ---- | ---------------- |
| -f   | File exists      |
| -d   | Directory exists |
| -r   | Readable         |
| -w   | Writable         |
| -x   | Executable       |
| -e   | Exists           |

Example:

```bash
if [ -f file.txt ]
then
    echo "File exists"
fi
```

---

# Exit Status

Every command returns an exit code.

```bash
echo $?
```

Common values:

| Code | Meaning           |
| ---- | ----------------- |
| 0    | Success           |
| 1    | Error             |
| 127  | Command not found |

Example:

```bash
mkdir test

if [ $? -eq 0 ]
then
    echo "Directory created"
fi
```

---

# Useful Commands in Scripts

## date

```bash
date
```

---

## hostname

```bash
hostname
```

---

## whoami

```bash
whoami
```

---

## uptime

```bash
uptime
```

---

## df

```bash
df -h
```

---

## free

```bash
free -h
```

---

# Debugging Scripts

## Bash Debug Mode

```bash
bash -x script.sh
```

---

## Enable Inside Script

```bash
set -x
```

Disable:

```bash
set +x
```

---

# Best Practices

### Quote Variables

Good:

```bash
echo "$name"
```

Bad:

```bash
echo $name
```

---

### Use Meaningful Variable Names

Good:

```bash
user_name="john"
```

Bad:

```bash
x="john"
```

---

### Check Command Success

```bash
if mkdir backup
then
    echo "Success"
else
    echo "Failed"
fi
```

---

### Use Functions

Break large scripts into reusable functions.

---

# Practical Examples

## Backup Script

```bash
#!/bin/bash

SOURCE="/home/user/data"
BACKUP="/home/user/backup"

cp -r "$SOURCE" "$BACKUP"

echo "Backup Completed"
```

---

## System Information Script

```bash
#!/bin/bash

echo "Hostname: $(hostname)"
echo "User: $(whoami)"
echo "Uptime:"
uptime
```

---

## Check Disk Usage

```bash
#!/bin/bash

usage=$(df / | tail -1 | awk '{print $5}')

echo "Disk Usage: $usage"
```

---

# Common Bash Interview Questions

### Difference between `sh` and `bash`

* `bash` is an enhanced version of `sh`
* Supports arrays, functions, command history, and advanced scripting features

### Difference between `$*` and `$@`

* `$*` treats all arguments as a single string
* `$@` treats each argument separately

### What does `#!/bin/bash` mean?

It specifies the interpreter used to execute the script.

### What is `$?`

The exit status of the last executed command.

### How do you make a script executable?

```bash
chmod +x script.sh
```

---

# Summary

Essential concepts to master:

* Shebang
* Variables
* User Input
* Arguments
* Conditionals
* Loops
* Functions
* Arrays
* File Handling
* Exit Codes
* Debugging
* Best Practices

After mastering shell scripting, move on to:

1. File Permissions
2. Process Management
3. Cron Jobs
4. Log Analysis
5. Bash Automation Projects
6. DevOps Automation

