# Processes and Jobs

## Listing Processes
First, we will learn to list running processes using the ps command.

```bash
hacker@dojo:~$ ps
    PID TTY          TIME CMD
    329 pts/0    00:00:00 bash
    349 pts/0    00:00:00 ps
hacker@dojo:~$
```

As ps is a very old utility, its usage is a bit of a mess. There are two ways to specify arguments.

"Standard" Syntax: in this syntax, you can use -e to list "every" process and -f for a "full format" output, including arguments. These can be combined into a single argument -ef.

"BSD" Syntax: in this syntax, you can use a to list processes for all users, x to list processes that aren't running in a terminal, and u for a "user-readable" output. These can be combined into a single argument aux.

```bash
hacker@dojo:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
hacker         1       0  0 05:34 ?        00:00:00 /sbin/docker-init -- /bin/sleep 6h
hacker         7       1  0 05:34 ?        00:00:00 /bin/sleep 6h
hacker       102       1  1 05:34 ?        00:00:00 /usr/lib/code-server/lib/node /usr/lib/code-server --auth=none -
hacker       138     102 11 05:34 ?        00:00:07 /usr/lib/code-server/lib/node /usr/lib/code-server/out/node/entr

hacker@dojo:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
hacker         1  0.0  0.0   1128     4 ?        Ss   05:34   0:00 /sbin/docker-init -- /bin/sleep 6h
hacker         7  0.0  0.0   2736   580 ?        S    05:34   0:00 /bin/sleep 6h
hacker       102  0.4  0.0 723944 64660 ?        Sl   05:34   0:00 /usr/lib/code-server/lib/node /usr/lib/code-serve
```

### Objective
In this level, I have once again renamed /challenge/run to a random filename, and this time made it so that you cannot ls the /challenge directory! But I also launched it, so you can find it in the running process list, figure out the filename, and relaunch it directly for the flag! 

### Solve
**Flag:** `pwn.college{U3PBPW_sWD3febm2qSMxHsJnmpP.dhzM4QDLygjN0czW}`

- In this challenge, I first ran the `ps -ef` command to list out the processes running and find the file name.
- After finding the file name, I simple launched it and got the flag.

```bash
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 19:18 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 19:18 ?        00:00:00 /run/dojo/bin/sleep 6h
root         132       1  0 19:18 ?        00:00:00 /challenge/7666-run-9119
root         135     132  0 19:18 ?        00:00:00 sleep 6h
hacker       137       0  0 19:18 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoin
hacker       143     137  0 19:18 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       159     143  0 19:20 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/7666-run-9119
Yahaha, you found me! Here is your flag:
pwn.college{U3PBPW_sWD3febm2qSMxHsJnmpP.dhzM4QDLygjN0czW}
Now I will sleep for a while (so that you could find me with 'ps').
```

### New Learnings
1. `ps` command is used to list out all the process running in the shell at a time.
2. It can be ran in two formats :
    1. `ps -ef` 
    2. `ps aux`
Both the ways list out basic info about the processes like user, process ID, start time, total time taken and process name, etc.