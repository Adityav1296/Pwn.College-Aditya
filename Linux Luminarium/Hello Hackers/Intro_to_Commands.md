# Hello Hackers

## Intro to Commands
In this challenge, we invoke our first program\
When you type a command and hit enter, the command will be invoked, as so:

```hacker@dojo:~$ whoami
hacker
hacker@dojo:~$
```

When the command terminates, the shell once again displays the prompt, ready for the next command.

### Solve
**Flag:** `pwn.college{wXHpr2GmZG9CvbuDVZRDWp0fCAZ.ddjNyUDLygjN0czW}`

-> In this challenge, we simply needed to execute the hello program to get the required flag. 
-> I also executed the 'whoami' command given in the challenge description to check the user.

```bash
hacker@hello~intro-to-commands:~$ whoami
hacker
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{wXHpr2GmZG9CvbuDVZRDWp0fCAZ.ddjNyUDLygjN0czW}```

### New Learning
Learnt how the commands can be executed through the command line.