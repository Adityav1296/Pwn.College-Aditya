# Terminal Multiplexing

## Launching Screen
Screen is a program that creates virtual terminals inside your terminal. It's somewhat like having multiple browser tabs, but for your command line!

Starting screen is super simple:

```bash
hacker@dojo:~$ screen
```

That's it! You're now inside a screen session. It looks exactly like a terminal, but there are new capabilities there, waiting to be discovered.

### Objective
For this challenge, we've hooked things up so that just launching screen will get you the flag. Easy!

### Solve
**Flag:** `pwn.college{YjykRS2i5_RDKCY7WiFSZIHS5gU.QX1gjM4EDLygjN0czW}`

- As is told in the challenge objective, I simply ran the `screen` command and started a screen session. There I directly got the flag once I entered the session.

```bash
hacker@terminal-multiplexing~launching-screen:~$ screen
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{YjykRS2i5_RDKCY7WiFSZIHS5gU.QX1gjM4EDLygjN0czW}
hacker@terminal-multiplexing~launching-screen:~$ exit
[screen is terminating]
```

### New Learnings
1. When we want to run multiple terminals inside our terminal, we can use the `screen` command to start a screen session for the command line.
2. When you're done with your command line, type exit or press Ctrl-D to leave the screen session. Then screen will terminate and return you to your original shell.