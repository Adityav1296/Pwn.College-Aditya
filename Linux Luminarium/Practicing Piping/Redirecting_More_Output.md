# Practicing Piping

## Redirecting More Output
Aside from redirecting the output of echo, you can, of course, redirect the output of any command.

### Objective 
In this level, /challenge/run will once more give you a flag, but only if you redirect its output to the file myflag. Your flag will, of course, end up in the myflag file!

### Solve
**Flag:** `pwn.college{Apma4zug9IUZIjES3K2NW2zCOIg.dVjN1QDLygjN0czW}`

- It is a simple challenge where I redirected the output from running the */challenge/run* command to the myflag file using the '>' character. Then I used the *cat* command with myflag as argument and got the flag.

```bash
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ ls
Desktop  flag  home-backup.tar.gz  myflag
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{Apma4zug9IUZIjES3K2NW2zCOIg.dVjN1QDLygjN0czW}
```

### New Learnings
1. Using '>' character to redirect outputs of not only *echo* command but any command it receives.  
2. Moreover, when we run a command, even after redirecting its output, the error message is still displayed if there is an error. This is because the error message is communicated over stderr which is a different channel than stdout used for outputs.