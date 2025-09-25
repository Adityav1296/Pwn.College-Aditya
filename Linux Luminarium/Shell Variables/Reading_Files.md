# Shell Variables

## Reading Files
Often, when shell users want to read a file into an environment variable, they do something like:

```bash
hacker@dojo:~$ echo "test" > some_file
hacker@dojo:~$ VAR=$(cat some_file)
hacker@dojo:~$ echo $VAR
test
```

This works, but it represents what grouchy hackers call a "Useless Use of Cat". Previously, you read user input into a variable. You've also previously redirected files into command input! Put them together, and you can read files with the shell.

```bash
hacker@dojo:~$ echo "test" > some_file
hacker@dojo:~$ read VAR < some_file
hacker@dojo:~$ echo $VAR
test
```

### Objective 
Read /challenge/read_me into the PWN environment variable, and we'll give you the flag! The /challenge/read_me will keep changing, so you'll need to read it right into the PWN variable with one command!

### Solve
**Flag:** `pwn.college{wXvRzcWF5raXWGaHa4ughOW8KrC.dBjM4QDLygjN0czW}`

- In this challenge, I first changed my directory to /challnege and listed the files present in it. Then I used `cat read_me` to show how the read_me file is constantly changing.
- Then, using the *read* command, I read the contents of the read_me file as input to PWN variable.
- After that I echoed the variable and used *cat* command on the file and this time they had the same content in them.

```
hacker@variables~reading-files:~$ cd /challenge
hacker@variables~reading-files:/challenge$ ls
DESCRIPTION.md  read_me  run
hacker@variables~reading-files:/challenge$ cat read_me
GpzpSmtQrKwNAA7W3t4QTzPmkz2diK6kleiwzwLKh6hXhacker@variables~reading-files:/challenge$ cat read_me
kIUvDG2DXsHph6M1t7M62nOPvne4SY0uSgExn8xbTquivYpNUL4Lyhacker@variables~reading-files:/challenge$ read PWN < read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wXvRzcWF5raXWGaHa4ughOW8KrC.dBjM4QDLygjN0czW}
hacker@variables~reading-files:/challenge$ echo $PWN
0xE6HpWsVa6NbkGGSHnR5Lk4sKMArXV019t0si5r4
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wXvRzcWF5raXWGaHa4ughOW8KrC.dBjM4QDLygjN0czW}
hacker@variables~reading-files:/challenge$ cat read_me
0xE6HpWsVa6NbkGGSHnR5Lk4sKMArXV019t0si5r4You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wXvRzcWF5raXWGaHa4ughOW8KrC.dBjM4QDLygjN0czW}
```

### New Learnings
1. We can combine the concept of redirection of input and the *read* command to read the contents of a file into a variable.
