# Practicing Piping

## Split-piping Stderr and Stdout 
Now, let's put your knowledge together. You must master the ultimate piping task: redirect stdout to one program and stderr to another.

The challenge here, of course, is that the | operator links the stdout of the left command with the stdin of the right command. Of course, you've used 2>&1 to redirect stderr into stdout and, thus, pipe stderr over, but this then mixes stderr and stdout. How to keep it unmixed?

### Objective 
In this challenge, you have:

  1. /challenge/hack: this produces data on stdout and stderr
  2. /challenge/the: you must redirect hack's stderr to this program
  3. /challenge/planet: you must redirect hack's stdout to this program

Go get the flag!

### Solve
**Flag:** `pwn.college{MLrstJaNQJkpQS4_JSoBr03_xtP.dFDNwYDLygjN0czW}`

- In this challenge, initially I tried to check if I can transfer the output and error messages separately in two different commands. However, that was not possible as it gave an error.
- Then I thought since we cannot use '2>&1' to disguise the error message as output message because then we will have two different output messages which we would have to transfer to two different files. We must transfer the error message to its location first.
- Therefore I used the '2>' operator to first transfer the error message to >(/challenge/the) and then piped and used *tee* command to transfer the output to >(/challenge/planet).

```bash
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack | tee >(/challenge/planet)
This secret data must directly make it to /challenge/planet over my stdout.
Dont try to copy-paste it; it changes too fast.
3187514218204366148
You must redirect my standard error into '/challenge/the'!
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) | tee >(/challenge/planet)
This secret data must directly make it to /challenge/planet over my stdout.
Dont try to copy-paste it; it changes too fast.
1140014857226742370
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{MLrstJaNQJkpQS4_JSoBr03_xtP.dFDNwYDLygjN0czW}
```

### New Learnings
1. In case we need to transfer both error and output messages of a command to other files or commands, then we should first try to tranfer the error message and then look for transfering the output message.