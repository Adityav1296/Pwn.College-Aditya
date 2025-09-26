# Processes and Jobs

## Interrupting Processes
Sometimes you just want to get rid of the process that's clogging up your terminal! Luckily, terminals have a hotkey for this: Ctrl-C (e.g., holding down the Ctrl key and pressing C) sends an "interrupt" to whatever application is waiting on input from the terminal and, typically, this causes the application to cleanly exit.

### Objective
/challenge/run will refuse to give you the flag until you interrupt it.

### Solve
**Flag:** `pwn.college{Ecloyg1cF2beQbQH_soKq8XXyaL.dNDN4QDLygjN0czW}`

- In this challenge, I simply ran the `/challenge/run` command and then used Ctrl+C to interrupt it and get the flag.

```bash
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{Ecloyg1cF2beQbQH_soKq8XXyaL.dNDN4QDLygjN0czW}
```

### New Learnings
1. Ctrl+C can be used to interrupt processes that are awaiting input from the terminal.