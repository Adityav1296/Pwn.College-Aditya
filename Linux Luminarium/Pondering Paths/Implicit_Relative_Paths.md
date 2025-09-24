# Pondering Paths

## Implicit Relative Path
In this level, we'll practice referring to paths using . a bit more. Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path. Consider the following:

```
hacker@dojo:~$ cd /challenge
hacker@dojo:/challenge$ run
```

This will not invoke /challenge/run. This is actually a safety measure: if Linux searched the current directory for programs every time you entered a naked path, you could accidentally execute programs in your current directory that happened to have the same names as core system utilities! As a result, the above commands will yield the following error:

```
bash: run: command not found
```

### Objective
In this challenge, we'll learn how to explicitly use relative paths to launch run in this scenario. The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using . like in the previous levels. This challenge will need you to run it from the /challenge directory.

### Solve
**Flag:** `pwn.college{Eoow8R418nc9XiyBy6NFM7ZURK_.dFTN1QDLygjN0czW}`

-> In this challenge, since it is given that the current working directory should be /challenge, therefore the first thing I did was to change my directory to /challenge using the *cd* command.  
-> Then I ran the *./run* command to get the flag.
-> I also tried using the "naked" path by just typing *run* and *.run* once i got to the /challegne directory but it gave an error as shown below.

```bash
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ run
bash: run: command not found
hacker@paths~implicit-relative-path:/challenge$ .run
bash: .run: command not found
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{Eoow8R418nc9XiyBy6NFM7ZURK_.dFTN1QDLygjN0czW}
```

### New Learning
1. "Naked" paths are not safe to execute as Linux might end up executing programs in our current directory that have the same name as core system utilities. 
2. Using '.' and '..' lets us specify the correct path to the target files and do the correct command execution.
