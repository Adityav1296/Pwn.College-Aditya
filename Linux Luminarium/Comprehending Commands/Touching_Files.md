# Comprehending Commands 

## Touching Files
You can also create files! There are several ways to do this, but we'll look at a simple command here. You can create a new, blank file by touching it with the touch command:

```
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ touch pwnfile
hacker@dojo:/tmp$ ls
pwnfile
hacker@dojo:/tmp$
```

### Objective
In this level, please create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get your flag!

### Solve
**Flag:** `pwn.college{gX1hh6rL7hh_O2wArcpBhUniA41.dBzM4QDLygjN0czW}`

-> In this challenge, since the absolute paths to the files that we need to create were given already, I used the *touch* command to directly create the two files from the home directory only.  
-> Then I changed my directory to /tmp and used *ls* command to confirm whether the files have been created or not. Once confirmed, I ran the */challenge/run* command to get the flag.

```bash
hacker@commands~touching-files:~$ touch /tmp/pwn /tmp/college
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ ls
bin  college  hsperfdata_root  pwn  tmp.TpSOPGOVKK
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{gX1hh6rL7hh_O2wArcpBhUniA41.dBzM4QDLygjN0czW}
hacker@commands~touching-files:/tmp$ cd ~
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{gX1hh6rL7hh_O2wArcpBhUniA41.dBzM4QDLygjN0czW}
```

### New Learning
1. *touch* command can be used to create files in the directories.  
2. We can create one or multiple files at a time by passing the file names to the *touch* command as arguments.