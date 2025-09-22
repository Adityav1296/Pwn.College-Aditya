# Pondering Paths

## Home Sweet Home
Every user has a home directory, typically under /home in the filesystem. In the dojo, you are the hacker user, and your home directory is /home/hacker. The home directory is typically where users store most of their personal files.

Typically, your shell session will start with your home directory as your current working directory. Consider the initial prompt:

```
hacker@dojo:~$
```

The ~ in this prompt is the current working directory, with ~ being shorthand for /home/hacker. Bash provides and uses this shorthand because, again, most of your time will be spent in your home directory. Thus, whenever bash sees ~ provided as the start of an argument in a way consistent with a path, it will expand it to your home directory. Consider : 

```
hacker@dojo:~$ echo LOOK: ~
LOOK: /home/hacker
hacker@dojo:~$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~
hacker@dojo:~$ cd /home/hacker/asdf
hacker@dojo:~/asdf$
```

Note that the expansion of ~ is an absolute path, and only the leading ~ is expanded. 

### Objective
In this challenge, /challenge/run will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:

- Your argument must be an absolute path.
- The path must be inside your home directory.
- Before expansion, your argument must be three characters or less

Again, you must specify your path as an argument to /challenge/run 

### Solve
**Flag:** `pwn.college{MilrmyDBSIEimk5Qges34x51O-o.dNzM4QDLygjN0czW}`

-> In this challenge, since we didn't need to change any directory, I straight away executed the command as required by the challenge : */challenge/run ~/a*  
-> Since the constraints required an argument with 3 characters and an absolute path, the only option for fullfilling the absolute path condition was to use '~' which expands to /home/hacker.  
-> Since a path was needed as argument, after '~' I added '/a' where a is the name of any random file in the home directory.

```bash
hacker@paths~home-sweet-home:~$ /challenge/run ~/a
Writing the file to /home/hacker/a!
... and reading it back to you:
pwn.college{MilrmyDBSIEimk5Qges34x51O-o.dNzM4QDLygjN0czW}
```

### New Learning
1. '~' is an absolute path expanding to /home/hacker in case of this dojo and in general it expands to the name of the home directory of the user.
2. Commands can accept '~' as an argument since it expands to the path of the home directory.