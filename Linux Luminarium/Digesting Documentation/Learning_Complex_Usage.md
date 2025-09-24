# Digesting Documentation 

## Learning Complex Usage
While using most commands is straightforward, the usage of some commands can get quite complex. This sounds crazy, but you've already encountered this with the find level in Basic Commands. find has a -name argument, and the -name argument itself takes an argument specifying the name to search for. Many other commands are analogous.

### Objective
Here is this level's documentation for /challenge/challenge:

>Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!

Given that documentation, go get the flag!

### Solve
**Flag:** `pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}`

-> In this challenge, the task to be performed was pretty direct and can be done in two ways :
  1. Starting from the home directory, we can just write in `/challenge/challenge --printfile flag` to obtain the flag.
  2. Or we can change the directory to /challenge, list out its content to check the challenge file present there and then run the command given in the challenge as is done below.

```bash
hacker@man~learning-complex-usage:~$ ls
Desktop  flag  home-backup.tar.gz
hacker@man~learning-complex-usage:~$ cd /challenge
hacker@man~learning-complex-usage:/challenge$ ls
DESCRIPTION.md  challenge
hacker@man~learning-complex-usage:/challenge$ ./challenge --printfile ../flag
Correct argument! Here is the /home/hacker/flag file:
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
```

### New Learning
1. In some cases, the argument to a command can have its own argument as well. Some examples are:
   1. grep -n search_string location_name -> Here, -n is an argument with search_string and location_name as its own arguments and displays the line number where the search_string is found.
   2. find location_name -name file_name -> Here, -name is an argument with the file_name and location_name is its own arguments.
