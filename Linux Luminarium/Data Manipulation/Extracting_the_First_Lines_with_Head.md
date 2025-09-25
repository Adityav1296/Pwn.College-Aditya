# Data Manipulation

## Extracting the First Lines with Head
The head command is used to display the first few lines of its input:

```bash
hacker@dojo:~$ cat /something/very/long | head
this
is
just
the
first
ten
lines
of
the
file
hacker@dojo:~$
```

HBy default, it shows the first 10 lines, but you can control this with the -n option:

```bash
hacker@dojo:~$ cat /something/very/long | head -n 2
this
is
hacker@dojo:~$
```

### Objective
This challenge's /challenge/pwn outputs a bunch of data, and you'll need to pipe it through head to grab just the first 7 lines and then pipe them onwards to /challenge/college, which will give you the flag if you do this right. Your solution will be a long composite command with two pipes connecting three commands. 

### Solve
**Flag:** `pwn.college{4l7tFI5hYrAJtFBQ8_TfNKXL6Ax.QX2ETM3EDLygjN0czW}`

- In this challenge, I straightaway used the piping operator to pipe the output of */challenge/pwn* command and on the other side, I used the *head -n* command and extracted the first 7 lines of the output of */challenge/pwn* command. Then I further piped the 7 extracted lines to the */challenge/collge* command and got the flag.

```bash
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{4l7tFI5hYrAJtFBQ8_TfNKXL6Ax.QX2ETM3EDLygjN0czW}
```

### New Learnings
1. The *head* command is used to extract the first few lines of the output of a file or program. We can use the '-n' option with it to specify the number of lines that we want to extract.