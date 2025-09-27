# Chaining Commands

## Chaining with Semicolons
The easiest way to chain commands is ;. In most contexts, ; separates commands in a similar way to how Enter separates lines. So, this:

```bash
hacker@dojo:~$ echo COLLEGE > pwn
hacker@dojo:~$ cat pwn
COLLEGE
hacker@dojo:~$
```

Is roughly the same as this:

```bash
hacker@dojo:~$ echo COLLEGE > pwn; cat pwn
COLLEGE
hacker@dojo:~$
```

Basically, when you hit Enter, your shell executes your typed command and, after that command terminates, gives you the prompt to input another command. The semicolon is analogous, just without the prompt and with you entering both commands before anything is executed.

### Objective
In this level, you must run /challenge/pwn and then /challenge/college, chaining them with a semicolon.

### Solve
**Flag:** `pwn.college{chJTAp0oACppOeHg9VTDXik4e5K.dVTN4QDLygjN0czW}`

- In this challenge, I just ran the two commands separated by a semicolon and got the flag.

```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{chJTAp0oACppOeHg9VTDXik4e5K.dVTN4QDLygjN0czW}
```

### New Learnings
1. The semicolon can be used to execute two or more programs one after another. This way, we don't need to execute one command and then wait for the prompt to execute the second one. We can execute them together.