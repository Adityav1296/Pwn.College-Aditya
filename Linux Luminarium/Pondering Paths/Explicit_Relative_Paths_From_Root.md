# Pondering Paths

## Explicit Relative Path From /
Previously, your relative path was "naked": it directly specified the directory to descend into from the current directory. In this level, we're going to explore more explicit relative paths.

In most operating systems, including Linux, every directory has two implicit entries that you can reference in paths: . and ... The first, ., refers right to the same directory, so the following absolute paths are all identical to each other:

```
/challenge
/challenge/.
/challenge/./././././././././
/./././challenge/././
```

The following relative paths are also all identical to each other:

```
challenge
./challenge
./././challenge
challenge/.
```

### Objective
You'll need to run /challenge/run using a relative path using '.' while having a current working directory of /. 

### Solve
**Flag:** `pwn.college{AXdMDHxYj7gZodGEdUiPJInfWK_.dBTN1QDLygjN0czW}`

-> In this challenge, since it is given that the current working directory should be root i.e /, therefore the first thing I did was to change my directory to root using the *cd* command.  
-> Then I ran the *./challenge/run* command to get the flag.  
-> I also tried *../challlenge/run* command and got the same output.

```bash
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{AXdMDHxYj7gZodGEdUiPJInfWK_.dBTN1QDLygjN0czW}
hacker@paths~explicit-relative-paths-from-:/$ ../challenge/run
Correct!!!
../challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{AXdMDHxYj7gZodGEdUiPJInfWK_.dBTN1QDLygjN0czW}
```

### New Learning
1. '.' = current working directory.  
   When using a single '.' in the relative path, we remain in the same directory. What it does is append the path after '.' to the current directory and tells where to find the file to run. Example :  
   Suppose we are in the /home/student directory and then we type ./challenge/run command, then it will result in /home/student/challenge/run command in full.  
2. '..' = parent directory.  
   When using double '..' in relative paths, we go one step above to the parent directory. From there, the command just references another path relative to it. Example :  
   Suppose we are in the /home/student/projects directory and the we type ../challenge/run command, then the path will become /home/student/challenge/run for executing the run file.  
   However, the working directory still remains the same i.e /home/student/projects unless we explicitly change the directory.  
3. If we are in the root directory, then both '.' and '..' will behave the same since root doesn't have any parent directory above it.  

### References
1. Chatgpt for understanding the difference between '.' and '..' and how they behave when the parent directory is root.
