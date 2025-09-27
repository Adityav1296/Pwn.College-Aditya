# Pondering PATH

## The PATH Variable
It turns out that the answer to "How does the shell find ls?" is fairly simple. There is a special shell variable, called PATH, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands. If you blank out the variable, things go badly:

```bash
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ PATH=""
hacker@dojo:~$ ls
bash: ls: No such file or directory
hacker@dojo:~$
```

Without a PATH, bash cannot find the ls command.


### Objective
In this level, you will disrupt the operation of the /challenge/run program. This program will DELETE the flag file using the rm command. However, if it can't find the rm command, the flag will not be deleted, and the challenge will give it to you! Thus, you must make it so that /challenge/run also can't find the rm command!

### Solve
**Flag:** `pwn.college{Em-j237lFeXS1vhUmg097NLaQe6.dZzNwUDLygjN0czW}`

- I first set the PATH variable to value null and then ran the /challenge/run command to get the flag.

```bash
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ sh
bash: sh: No such file or directory
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{Em-j237lFeXS1vhUmg097NLaQe6.dZzNwUDLygjN0czW}
```

### New Learnings
1. PATH is a shell variable that contains the path to all the directories where the programs related to the commands are stored. 
2. If we set the value of PATH to null, the commands will face error while executing as they won't be able to find the paths to their respective programs needed to run them.