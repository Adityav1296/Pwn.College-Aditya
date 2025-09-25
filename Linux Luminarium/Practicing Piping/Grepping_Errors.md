# Practicing Piping

## Grepping Errors
The > operator redirects a given file descriptor to a file, and you've used 2> to redirect fd 2, which is standard error. The | operator redirects only standard output to another program, and there is no 2| form of the operator! It can only redirect standard output.

The shell has a >& operator, which redirects a file descriptor to another file descriptor. This means that we can have a two-step process to grep through errors: first, we redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal!

### Objective 
Like the last level, this level will overwhelm you with output, but this time on standard error. grep through it to find the flag!

### Solve
**Flag:** `pwn.college{UmIh5guFiKZBfrquUwRcW8XTdsl.dVDM5QDLygjN0czW}`

- Here the first thing that came to mind was how to chain all these commands and get the flag required. 
- Like the challenge before we needed to run the /challenge/run command and then I used '2>& 1' to disguise its error message as an output message and piped it. 
- On the other side of pipe operator, I used the grep command to find the flag.

```bash
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep -n pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
1991:pwn.college{UmIh5guFiKZBfrquUwRcW8XTdsl.dVDM5QDLygjN0czW}
```

### New Learnings
1. We can use '>&' to redirect one file descipter to another. In this way, we can basically disguise the error messages as legal output messages using '2>& 1'. 
2. Since pipe operator can only pass the output messages, this way of disguising the error messages allows us to pipe them without any problem.
