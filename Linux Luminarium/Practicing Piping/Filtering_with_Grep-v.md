# Practicing Piping

## Filtering with grep -v
The grep command has a very useful option: -v (invert match). While normal grep shows lines that MATCH a pattern, grep -v shows lines that do NOT match a pattern:

```bash
hacker@dojo:~$ cat data.txt
hello hackers!
hello world!
hacker@dojo:~$ cat data.txt | grep -v world
hello hackers!
hacker@dojo:~$
```

### Objective 
In this challenge, /challenge/run will output the flag to stdout, but it will also output over 1000 decoy flags (containing the word DECOY somewhere in the flag) mixed in with the real flag. You'll need to filter out the decoys while keeping the real flag!  
Use grep -v to filter out all the lines containing "DECOY" and reveal the real flag!

### Solve
**Flag:** `pwn.college{gxRYXVZIH-DEKSPXi8ibJG6bPnC.QX4ETM3EDLygjN0czW}`

- Here I directly went for the `grep -v DECOY` command after piping the output of the /challenge/run command to filter through the decoy flags and find the correct one.
- Btw, I intentionally ran the `grep -n pwn.college` command after the pipe and ended up displaying over 1200 flags.

```bash
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{gxRYXVZIH-DEKSPXi8ibJG6bPnC.QX4ETM3EDLygjN0czW}
```

### New Learnings
1. Unlike `grep search_string` command which is used to find a string throughout the output or contents of the commands and files, `grep -v string` command is used to ignore all those lines that contain the string given as argument to -v.
2. It displays all those lines that do not contain the target string.