# Shell Variables

## Multi-Word Variables
Spaces have special significance in the shell, and there are places where you can't use them spuriously. To set a multi word value to a variable, you might try :

```bash
hacker@dojo:~$ VAR=1337 SAUCE
```

This looks reasonable, but it does not work, for similar reasons to needing to have no spaces around the =. When the shell sees a space, it ends the variable assignment and interprets the next word (SAUCE in this case) as a command. To set VAR to 1337 SAUCE, you need to quote it:

```bash
hacker@dojo:~$ VAR="1337 SAUCE"
```

### Objective 
In this level, you'll need to set the variable PWN to COLLEGE YEAH. Good luck!

### Solve
**Flag:** `pwn.college{gcKeMYJcW9gwH5FRtj97tOZLn3g.dBjN1QDLygjN0czW}`

- In this challenge, I directly set the value of PWN to COLLEGE YEAH by putting them in " ".

```bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You have set the PWN variable properly! As promised, here is the flag:
pwn.college{gcKeMYJcW9gwH5FRtj97tOZLn3g.dBjN1QDLygjN0czW}
```

### New Learnings
1. To assign muliple word values to the variables, we need to place the entire value in " ", just like how strings values are assigned to a varible in other programming languages.