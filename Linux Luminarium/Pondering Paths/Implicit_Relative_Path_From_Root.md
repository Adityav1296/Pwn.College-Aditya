# Pondering Paths

## Implicit Relative Path From /
If you put in absolute paths everywhere, then it really doesn't matter what directory you are in. However, the current working directory does matter for relative paths.

- A relative path is any path that does not start at root (i.e., it does not start with /).
- A relative path is interpreted relative to your current working directory (cwd).
- Your cwd is the directory that your prompt is currently located at.

This means how you specify a particular file, depends on where the terminal prompt is located.

### Objective
Let's try it here! You'll need to run /challenge/run using a relative path while having a current working directory of /. 

### Solve
**Flag:** `pwn.college{o9Eby5PtSXj0aAOh07y3Qt4MuDd.dlDN1QDLygjN0czW}`

-> In this challenge, since it is given that the current working directory should be root i.e /, therefore the first thing I did was to change my directory to root using the *cd* command.  
-> Then I ran the */challenge/run* command to get the flag.

```bash
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{o9Eby5PtSXj0aAOh07y3Qt4MuDd.dlDN1QDLygjN0czW}
```

### New Learning
1. In order to use the relative paths it is necessary that we are in the correct directory to begin the command. For example : here we were initially in the home(~) directory but since the relative path started with /, then we had to change the directory to root.
2. Imagine we want to access some file located at /tmp/a/b/my_file.
 - If my cwd is /, then a relative path to the file is tmp/a/b/my_file.
 - If my cwd is /tmp, then a relative path to the file is a/b/my_file.
 - If my cwd is /tmp/a/b/c, then a relative path to the file is ../my_file. The .. refers to the parent directory.