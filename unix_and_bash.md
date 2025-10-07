#  Introduction
## Basic usage and Syntax
Basic commands consist of the command,followed by arguments separated by spaces.

Commands should be separated by either a semicolon";" or a new line.

#  Files
## Important file management commands
- Creating a directory: `mkdir`
- Changing to another directory: `cd`
- Change to the parent directory: `cd ..`
- Listing the content: `ls`
    - Present all files: `ls -a`
    - Present long format(detail information for files): `ls -l`
- Creating an empty file: `touch`
```bash
touch fileA.txt
touch fileA.txt fileB.txt
```
- Listing specific content: `ls`
```bash
ls *.txt  # all .txt file
ls file[A,B]* # output all filename contain fileA or fileB
ls subdir # output all files in subdir
```
- Copying a file: `cp`
```bash
cp fileA.txt copy.txt # fileA.txt is the original file, and copy.txt is the copyfile of fileA.txt
cp fileA.txt /home/users/ # copy fileA.txt to the /home/users/ directory
cp fileA.txt /home/users/copy.txt # copy fileA.txt to the directory and rename the file
```
- Copying a directory: `cp -r`
```bash
cp -r subdir newdir # subdir is the original directory and newdir is the new directory, both in the same path; -r means recursive
cp -r subdir /home/users/ # copy all files under subdir to /home/users
cp -a subdir newdir # copy and keep the attribute of all file(access, timestamp)
```
- Moving a file or directory: `mv`
    rename a file or move a file to another path
```bash
mv copy.txt fileE.txt # It seems like renaming a file. copy.txt is the original file and the fileE.txt is the new file. copy.txt will not exist anymore, it will be called fileE.txt
mv copy.txt /home/users/fileE.txt # change the path of copy.txt and rename the file to fileE.txt at the same time.
mv oldfolder newfolder # rename a folder
mv myfolder /home/users/ # move a folder to a new path
```
- Removing a file: `rm`
```bash
rm filename
```
- Removing a directory: `rm -r`
```bash
rm -r subdir
```

# Input, Output and Redirection
Standard input(STDIN): keyboard
Standard output(STDOUT):screen
Standard error(STDERR):screen
## Redirection STDOUT
- Redirecting STDOUT to a File: `> or 1>`
```bash
echo "Hello world!" > out.txt
```
- Redirecting STDERR to a File:`2>`
```bash
ls out.txt 2> ls.err # note: between 2 and > no space
```
- Redirecting STDERR and STDOUT to a File: `&>`
```bash
ls out.txt &> all.log # all output to all.log
ls out.txt other.txt > all.txt 2>&1 # STDOUT to all.txt and 2>(error)will also show in the same place of the STDOUT(It is same as &>)
ls out.txt > ls.out 2> ls.err # output of "ls out.txt" to ls.out, error of "ls out.txt" to ls.err
```
## Redirection STDIN
  Redirecting STDIN: `<`
```bash
head -n2 < ls.txt
```
## Append STDOUT or STDERR to an existing File: `>>`
```bash
ls out.txt other.txt >> all.txt 2>&1
```
## Redirecting STDOUT to STDIN: `using pipes |`
```bash
ls | heade -n2 | sed 's/ls/blah/'
head -n2 < ls.txt | sed 's/l/L/'
echo "5 + 21 *31 | bc
```
# Variables
`=` without spaces before and after; use quotes`"` to include spaces; backslashes`\` to escape special characters.
## Variable expansion
- variable: `$a`
- variable (with borders): `${a}`
```bash
a=10
echo D${a}n # avoid ambiguity 
```
- variable (variable length): `${#a}`
- substring: `${a:0:3}`
- Arithmetic expansion: `$((expression))`
```bash
echo $((3+5)) # output is 8
```
- special variable (insert bash)
  `$0`: current script or command

  `$1~$9`: 1-9 parameter of script
## Command Substitution:`a=$(command)`
Bash offers an easy way to store the results of a command in a variable.
```bash
a=$(date)
echo $a # return the output of command "date" 
number=$(seq 1 10)
echo $number # return 1 2 3...
result=$(seq -s+ 1 10 | bc)
echo $result # the sum of 1-10
```
# Conditionals
`if [ .. ]; then..; else..;fi`
They are to be written on different lines or separeted by semicolons`;`
```bash

```