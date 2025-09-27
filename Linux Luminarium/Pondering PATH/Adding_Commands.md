# Pondering PATH

## Adding Commands
What we see here, of course, is the hacker making the shell more useful for themselves by bringing their own commands to the party. Over time, you might amass your own elegant tools. Let's start with win!

```bash
hacker@dojo:~$ ls /home/hacker/scripts
goodscript	badscript	okayscript
hacker@dojo:~$ PATH=/home/hacker/scripts
hacker@dojo:~$ goodscript
YEAH! This is the best script!
hacker@dojo:~$
```

### Objective
Previously, the win command that /challenge/run executed was stored in /challenge/more_commands. This time, win does not exist! Recall the final level of Chaining Commands, and make a shell script called win, add its location to the PATH, and enable /challenge/run to find it!

### Solve
**Flag:** `pwn.college{wVqOGJ2yk91l5kQNXC8LLSg-pTh.dZzNyUDLygjN0czW}`

- First I made the win file and the added executable permission to the file.
- Then I ran the `nano win` command to open the text editor and write the script in it. I also displayed the script written using the `cat` command.
- Then I added the path of the win script to the PATH variable and used the `which` command to conform it.
- At the end, I ran the /challenge/run command and got the flag.

```bash
hacker@path~adding-commands:~$ touch win
hacker@path~adding-commands:~$ ls -l win
-rw-r--r-- 1 hacker hacker 0 Sep 27 11:01 win
hacker@path~adding-commands:~$ chmod a+x win
hacker@path~adding-commands:~$ ls -l win
-rwxr-xr-x 1 hacker hacker 0 Sep 27 11:01 win
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ cat win
#!/bin/bash

cat /flag
hacker@path~adding-commands:~$ export PATH=/home/hacker:$PATH
hacker@path~adding-commands:~$ which win
/home/hacker/win
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{wVqOGJ2yk91l5kQNXC8LLSg-pTh.dZzNyUDLygjN0czW}
hacker@path~adding-commands:~$
```

### New Learnings
1. We can add the required path to the already existing path in the PATH variable without deleting the existing paths in the following 2 ways :
    1. $PATH:required_path : It adds the specified path at in the end of the PATH variable
    2. required_path:$PATH : It adds the specified path at the beginning of the PATH variable.