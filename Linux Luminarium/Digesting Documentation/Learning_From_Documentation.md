# Digesting Documentation 

## Learning From Documentation
The typical need you'll have for documentation is just to figure out how to use all these dang programs, and a specific case of that is figuring out what arguments to specify on the command line. The correct usage of programs depends, in a large part, on the proper specification of arguments to them.  
Recall the -a of ls -a in the hidden files challenge. That -a was an argument that told ls to list out hidden files as well as non-hidden files. 

### Objective
The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give you the flag. Let's pretend that this is its documentation:

>Welcome to the documentation for /challenge/challenge! To properly run this program, you will need to pass it the argument of --giveflag. Good luck!

Given that knowledge, go get the flag!

### Solve
**Flag:** `pwn.college{UENIZmjl2wg-yuZYu4AcgSFU3it.dRjM5QDLygjN0czW}`

-> In this challenge, the task to be performed was pretty direct and can be done in two ways :
  1. Starting from the home directory, we can just write in `/challenge/challenge --giveflag` to obtain the flag.
  2. Or we can change the directory to /challenge, list out its content to check the challenge file present there and then run the command given in the challenge as is done below.

```bash
hacker@man~learning-from-documentation:~$ cd /challenge
hacker@man~learning-from-documentation:/challenge$ ls
DESCRIPTION.md  challenge
hacker@man~learning-from-documentation:/challenge$ ./challenge --giveflag
Correct argument! Here is your flag:
pwn.college{UENIZmjl2wg-yuZYu4AcgSFU3it.dRjM5QDLygjN0czW}
```

### New Learning
1. The same command can be used in various scenarios to access different kind of information depending on the type of argument provided to the command. Some examples are:
   1. grep -n search_string location_name
   2. find -name file_name location_name
