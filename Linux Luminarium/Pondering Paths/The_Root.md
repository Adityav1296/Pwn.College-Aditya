# Pondering Paths

## The Root
The filesystem starts at /. Under that, there are a whole mess of other directories, configuration files, programs, and, most importantly, flags.\
You can invoke a program by providing its path on the command line.\
Path, one that starts with the root directory, is referred to as an "absolute path".

### Objective
In this level, we've added a program right in /, called pwn, that will give you the flag. You'll be giving the exact path, starting from /, so the path would be /pwn.

### Solve
**Flag:** `pwn.college{gwYTXFirh6NVsvwocG3j5is4eEp.dhzN5QDLygjN0czW}`

-> In this challenge, I executed the absolute path given in the challenge objective to obtain the flag. 

```bash
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{gwYTXFirh6NVsvwocG3j5is4eEp.dhzN5QDLygjN0czW}
```

### New Learning
1. The Linux filesystem behaves like a tree with a root(denoted by "/") at the very base.  
2. Directories can contain other directories, files and programs.  
3. Writing absolute paths. (Paths beginning with "/")