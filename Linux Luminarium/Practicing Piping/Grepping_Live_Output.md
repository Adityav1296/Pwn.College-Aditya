# Practicing Piping

## Grepping Live Output
It turns out that you can "cut out the middleman" and avoid the need to store results to a file, like you did in the last level. You can do this by using the | (pipe) operator. Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe. For example:

```bash
hacker@dojo:~$ echo no-no | grep yes
hacker@dojo:~$ echo yes-yes | grep yes
yes-yes
hacker@dojo:~$ echo yes-yes | grep no
hacker@dojo:~$ echo no-no | grep no
no-no
```

### Objective 
/challenge/run will output a hundred thousand lines of text, including the flag. grep for the flag!

### Solve
**Flag:** `pwn.college{4gt43VZtLRu6u00nAaVUX6yYAEA.dlTM4QDLygjN0czW}`

- In this challenge, I redirected the output of the /challenge/run command without storing it by using the '|' operator. 
- Then on the other side by using `grep -n` command I was able to find the flag and the line number in which it was at. 

```bash
hacker@piping~grepping-live-output:~$ /challenge/run | grep -n pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
71475:pwn.college{4gt43VZtLRu6u00nAaVUX6yYAEA.dlTM4QDLygjN0czW}
```

### New Learnings
1. We can redirect the output of a command directly without storing it by using the pipe '|' operator. 
2. Then we can use other commands to operate on the redirected output and find meaningful results from it.