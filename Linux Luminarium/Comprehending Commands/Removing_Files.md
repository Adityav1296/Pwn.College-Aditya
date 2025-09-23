# Comprehending Commands 

## Removing Files
Files are all around you. Like candy wrappers, there'll eventually be too many of them. In Linux, you remove files with the rm command, as so:

```
hacker@dojo:~$ touch PWN
hacker@dojo:~$ touch COLLEGE
hacker@dojo:~$ ls
COLLEGE     PWN
hacker@dojo:~$ rm PWN
hacker@dojo:~$ ls
COLLEGE
hacker@dojo:~$
```

### Objective
This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check, which will make sure you've deleted it and then give you the flag!

### Solve
**Flag:** `pwn.college{g2LFXvTOVeixPVN8KqtaYB1JBr2.dZTOwUDLygjN0czW}`

-> In this challenge, I first listed the contents of the home directory using *ls* command.  
-> Then I used the *rm* command to remove the delete_me file as required by the challenge.  
-> After that I ran the /challenge/check command to obtain the flag.

```bash
hacker@commands~removing-files:~$ ls
Desktop  delete_me  flag  home-backup.tar.gz
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{g2LFXvTOVeixPVN8KqtaYB1JBr2.dZTOwUDLygjN0czW}
```

### New Learning
1. *rm* command is used to delete files from the directories.  
2. We can delete multiple files at the same time by passing there names or paths to the *rm* command as arguments. 

```
hacker@commands~removing-files:~$ touch a b
hacker@commands~removing-files:~$ ls
Desktop  a  b  flag  home-backup.tar.gz
hacker@commands~removing-files:~$ rm a b
hacker@commands~removing-files:~$ ls
Desktop  flag  home-backup.tar.gz
```