# Practicing Piping

## Duplicating piped data with Tee
When you pipe data from one command to another, you of course no longer see it on your screen. This is not always desired. Luckily, there is a solution! The tee command duplicates data flowing through your pipes to any number of files provided on the command line. For example:

```bash
hacker@dojo:~$ echo hi | tee pwn college
hi
hacker@dojo:~$ cat pwn
hi
hacker@dojo:~$ cat college
hi
hacker@dojo:~$
```

You can imagine how you might use this to debug things going haywire:

```bash
hacker@dojo:~$ command_1 | command_2
Command 2 failed!
hacker@dojo:~$ command_1 | tee cmd1_output | command_2
Command 2 failed!
hacker@dojo:~$ cat cmd1_output
Command 1 failed: must pass --succeed!
hacker@dojo:~$ command_1 --succeed | command_2
Commands succeeded!
```

### Objective 
This process' /challenge/pwn must be piped into /challenge/college, but you'll need to intercept the data to see what pwn needs from you!

### Solve
**Flag:** `pwn.college{U2yeLBobi2z24KVgYXiQQgzkD78.dFjM5QDLygjN0czW}`

- Here the plan was simple. Since the /challenge/college command was not working on receiving the piped input from /challenge/pwn, there must be some problem when running the first command i.e the /challenge/pwn command.
- Therefore by using the *tee* command, I redirected the data flowing from the /challenge/pwn command to the pwn_output file before letting it get piped to /challenge/college command.
- There I found the secret argument that was needed to correctly run the commands and get the flag.
- Using the new `/challenge/pwn --secret U2yeLBob` command and piping it, I was able to obtain the flag.

```bash
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee pwn_output | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat pwn_output
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "U2yeLBob"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret U2y
eLBob | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{U2yeLBobi2z24KVgYXiQQgzkD78.dFjM5QDLygjN0czW}
```

### New Learnings
1. The *tee* command is used to intercept the data flowing between two pipes. This intercepted data can come in handy as it might contain additional information about the process taking place or some hidden arguments due to which an error might be showing.