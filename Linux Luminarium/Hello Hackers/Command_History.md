# Hello Hackers

## Command History
You're going to type a lot of commands, and typing everything from scratch can be annoying and time consuming. Luckily, the shell saves a history of every command you invoke.\
You can scroll through those saved commands with the up/down arrow keys.

### Objective
This challenge will inject the flag into your history. Bring up a terminal, hit the up arrow, and grab it!

### Solve
**Flag:** `pwn.college{A310o9TCODB3I3tCJL9zpB2xDsk.QX2MTM3EDLygjN0czW}`

-> In this challenge, we simply needed to press the up arrow key to get the required flag. 
-> I also checked out this function with the previous challenges that were solved to execute their respective programs.

```bash
hacker@hello~command-history:~$ the flag is pwn.college{A310o9TCODB3I3tCJL9zpB2xDsk.QX2MTM3EDLygjN0czW}
```

### New Learning
Learnt how to navigate through multiple commands that were previously executed.