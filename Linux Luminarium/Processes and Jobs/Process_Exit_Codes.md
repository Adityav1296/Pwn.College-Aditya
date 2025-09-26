# Processes and Jobs

## Process Exit Codes
Every shell command, including every program and every builtin, exits with an exit code when it finishes running and terminates. This can be used by the shell, or the user of the shell to check if the process succeeded in its functionality.

You can access the exit code of the most recently-terminated command using the special ? variable:

```bash
hacker@dojo:~$ touch test-file
hacker@dojo:~$ echo $?
0
hacker@dojo:~$ touch /test-file
touch: cannot touch '/test-file': Permission denied
hacker@dojo:~$ echo $?
1
hacker@dojo:~$
```

As you can see, commands that succeed typically return 0 and commands that fail typically return a non-zero value, most commonly 1 but sometimes an error code that identifies a specific failure mode.

### Objective
In this challenge, you must retrieve the exit code returned by /challenge/get-code and then run /challenge/submit-code with that error code as an argument. Good luck!

### Solve
**Flag:** `pwn.college{wA4bLlFVcn24XKgqob-3BtacFYi.dljN4UDLygjN0czW}`

- In this challenge, I first ran the `/challenge/get-code` command. Then I used `echo` command with '$?' as argument to get the exit code.
- I used this exit code as the argument to `/challenge/submit-code` command as is required by the challenge and obtained the flag.

```bash
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
75
hacker@processes~process-exit-codes:~$ /challenge/submit-code 75
CORRECT! Here is your flag:
pwn.college{wA4bLlFVcn24XKgqob-3BtacFYi.dljN4UDLygjN0czW}
```

### New Learnings
1. We can view the exit code of the most recently executed command by using the `echo $?` command. Generally, 0 is for successful execution and 1 is for failed execution. Error codes can also be generated that identify a specific failure mode.