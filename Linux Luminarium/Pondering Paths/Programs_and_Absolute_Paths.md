# Pondering Paths

## Program and Absolute Paths
Let's explore a slightly more complicated path! Except for in the previous level, challenges in pwn.college are in the challenge directory and the challenge directory is, in turn, right in the root directory (/). The path to the challenge directory is, thus, /challenge. The name of the challenge program in this level is run, and it lives in the /challenge directory. 

### Objective
This challenge requires you to execute it by invoking its absolute path. You'll want to execute the run file that is in the challenge directory that is, in turn, in the / directory.

### Solve
**Flag:** `pwn.college{wRZ7scgbEd04iaXvhkt1mxWt4eb.dVDN1QDLygjN0czW}`

-> In this challenge, since the run file is stored inside the challenge directory, so the absolute path to the file becomes : */challenge/run*  

```bash
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{wRZ7scgbEd04iaXvhkt1mxWt4eb.dVDN1QDLygjN0czW}
```

### New Learning
1. There can be multiple files and programs stored inside each directory which can be accessed be typing in the correct absolute path that leads to the target file.  
2. The absolute path to the target file should include all the intermediate directories that lie in the way to the target file.