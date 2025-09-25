# Practicing Piping

## Redirecting Output
First, let's look at redirecting stdout to files. You can accomplish this with the > character, as so:

```bash
hacker@dojo:~$ echo hi > asdf
```

This will redirect the output of echo hi (which will be hi) to the file asdf. You can then use a program such as cat to output this file:

```
hacker@dojo:~$ cat asdf
hi
```

### Objective 
In this challenge, you must use this output redirection to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase).

### Solve
**Flag:** `pwn.college{80eofOqut2ofR_7XNw_4eavsldS.dRjN1QDLygjN0czW}`

- It is a simple challenge where we just need to use the *echo* command to write the word PWN to the file COLLEGE with the help of '>' character.

```bash
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{80eofOqut2ofR_7XNw_4eavsldS.dRjN1QDLygjN0czW}
```

### New Learnings
1. Using '>' character to redirect outputs.