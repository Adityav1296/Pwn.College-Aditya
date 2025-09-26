# Processes and Jobs

## Suspending Processes
We interrupt processes with Ctrl-C, but there are less drastic measures you can use to get your terminal back! You can suspend processes to the background with Ctrl-Z.

### Objective
This level's run wants to see another copy of itself running and using the same terminal. How? Use the terminal to launch it, then suspend it, then launch another copy while the first is suspended!

### Solve
**Flag:** `pwn.college{In48AP4btbszUArFyRkRrgr5FXj.dVDN4QDLygjN0czW}`

- In this challenge, I simply ran the `/challenge/run` command once and then sent it to background using Ctrl+Z. Then I reran the same command and got the flag.

```bash
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         138     129  0 20:21 pts/0    00:00:00 bash /challenge/run
root         140     138  0 20:21 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         138     129  0 20:21 pts/0    00:00:00 bash /challenge/run
root         145     129  0 20:21 pts/0    00:00:00 bash /challenge/run
root         147     145  0 20:21 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{In48AP4btbszUArFyRkRrgr5FXj.dVDN4QDLygjN0czW}
```

### New Learnings
1. We use Ctrl+Z to send the processes to backgroung instead of interrupting them with Ctrl+C. This way, we can call those processes back when we want to.