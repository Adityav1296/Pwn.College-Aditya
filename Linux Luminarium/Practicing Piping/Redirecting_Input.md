# Practicing Piping

## Redirecting Input
Just like you can redirect output from programs, you can redirect input to programs! This is done using <, as so:

```bash
hacker@dojo:~$ echo yo > message
hacker@dojo:~$ cat message
yo
hacker@dojo:~$ rev < message
oy
```

### Objective 
In this level, we will practice using /challenge/run, which will require you to redirect the PWN file to it and have the PWN file contain the value COLLEGE! To write that value to the PWN file.

### Solve
**Flag:** `pwn.college{IUgR5UGwwOE6cV02gddlvUpjHk0.dBzN1QDLygjN0czW}`

- In this challenge, I echoed the word COLLEGE to the PWN file using the *echo* command. Then I also used *ls* to list out the contents of the home directory.
- Then I directly ran the `/challenge/run` command and redirected the input of PWN file to it using the '<' character.

```bash
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ ls
Desktop  PWN  flag  home-backup.tar.gz
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{IUgR5UGwwOE6cV02gddlvUpjHk0.dBzN1QDLygjN0czW}
hacker@piping~redirecting-input:~$ cd /challenge
hacker@piping~redirecting-input:/challenge$ ./run < ~/PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{IUgR5UGwwOE6cV02gddlvUpjHk0.dBzN1QDLygjN0czW}
```

### New Learnings
1. Inputs to a file can be redirected as well using the '<' character.
2. However, the input can only be redirected to a command that reads them out. That means the contents of the source file are fed to the stdin of the command. Therefore input redirection always requires a command on the left side to receive the input. Example :
    1. `cat < file.txt` is the same as `cat file.txt`
