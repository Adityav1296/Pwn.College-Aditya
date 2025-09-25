# Practicing Piping

## Grepping Stored Results
You know how to run commands, how to redirect their output (e.g., >), and how to search through the resulting file (e.g., grep). Let's put this together!

### Objective 
1. Redirect the output of /challenge/run to /tmp/data.txt.
2. This will result in a hundred thousand lines of text, with one of them being the flag, in /tmp/data.txt.
3. grep that for the flag!

### Solve
**Flag:** `pwn.college{ssQh57KZbmfqzaZ1mus3vkGAkmv.dhTM4QDLygjN0czW}`

- In this challenge, I redirected the output from `/challenge/run` command to the target file using '>' character.
- Then I used `grep -n` command to find the flag in the target file along with the line number where it was found.
- The instructions dispalyed by the /challenge/run command mention a reward file /challenge/.data.txt . However, I am unable to read the contents of that file using *cat* command, neither can I redirect its content to any other file. I think this /challenge/.data.txt file are the instructions only.

```bash
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ cat /challenge/.data.txt
cat: /challenge/.data.txt: Permission denied
hacker@piping~grepping-stored-results:~$ cat /challenge/.data.txt > data
cat: /challenge/.data.txt: Permission denied
hacker@piping~grepping-stored-results:~$ grep -n pwn.college /tmp/data.txt
51677:pwn.college{ssQh57KZbmfqzaZ1mus3vkGAkmv.dhTM4QDLygjN0czW}
```

### New Learnings
1. We can redirect the output or error message of a file or a command into another file and use grep command to locate the desired string inside the new file.