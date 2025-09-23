# Comprehending Commands 

## Catting Absolute Paths
In the last level, you did cat flag to read the flag out of your home directory! You can, of course, specify cat's arguments as absolute paths:

```
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
In the last level, you did `cat flag` to read the flag out of your home directory!
You can, of course, specify `cat`'s arguments as absolute paths:
```

### Objective
In this directory, I will not copy the flag to your home directory, but I will make it readable through the flag file. Read it with cat at it absolute path.

### Solve
**Flag:** `pwn.college{8_4T8GkgZKqPNMV-fHNoI2lcglx.dlTM5QDLygjN0czW}`

-> In this challenge, since it is mentioned to use the absolute path to the flag file therefore I used the absolute path : /flag.  
-> I also changed my directory to root(/) and the ran the *cat* command on the flag file. There also I was able to obtain the flag.

```bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{8_4T8GkgZKqPNMV-fHNoI2lcglx.dlTM5QDLygjN0czW}
hacker@commands~catting-absolute-paths:~$ cd /
hacker@commands~catting-absolute-paths:/$ cat flag
pwn.college{8_4T8GkgZKqPNMV-fHNoI2lcglx.dlTM5QDLygjN0czW}
```

### New Learning
1. Cat command can be used on absolute paths as well to read out the contents of one or more files. Else we can just change our directory to the required one and directly run the *cat* command on the target file there.
