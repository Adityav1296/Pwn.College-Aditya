# Pondering PATH

## Setting PATH
 PATH stores a list of directories to find commands in and, for commands in nonstandard places, we must typically execute them via their path:

```bash
hacker@dojo:~$ ls /home/hacker/scripts
goodscript	badscript	okayscript
hacker@dojo:~$ goodscript
bash: goodscript: command not found
hacker@dojo:~$ /home/hacker/scripts/goodscript
YEAH! This is the best script!
hacker@dojo:~$
```

If you maintain useful scripts that you want to be able to launch by bare name, this is annoying. However, by adding directories to or replacing directories in this list, you can expose these programs to be launched using their bare name! For example:

```bash
hacker@dojo:~$ PATH=/home/hacker/scripts
hacker@dojo:~$ goodscript
YEAH! This is the best script!
hacker@dojo:~$
```

### Objective
This level's /challenge/run will run the win command via its bare name, but this command exists in the /challenge/more_commands/ directory, which is not initially in the PATH. The win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory. 

### Solve
**Flag:** `pwn.college{8E7-cmiAbCqe6ZZbDGlGoQCXMjU.dVzNyUDLygjN0czW}`

- First I changed my directory to /challenge/more_commands and listed the files there to find the win file.
- Then I again came back to the home directory and to the PATH variable, I added the path to the win file.
- Then I ran the /challenge/run command and got the flag.

```bash
hacker@path~setting-path:~$ cd /challenge/more_commands
hacker@path~setting-path:/challenge/more_commands$ ls
win
hacker@path~setting-path:/challenge/more_commands$ cd
hacker@path~setting-path:~$ PATH="/challenge/more_commands"
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{8E7-cmiAbCqe6ZZbDGlGoQCXMjU.dVzNyUDLygjN0czW}
```

### New Learnings
1. We can set new paths in the PATH variable the same way we set values to a shell variable.
2. Setting paths to the PATH variable is beneficial when we want to execute scripts anywhere in the shell. By setting the path to the PATH variable, we don't need to type the entire path of the script whenever we want to run it. They can then be executed by their names only.