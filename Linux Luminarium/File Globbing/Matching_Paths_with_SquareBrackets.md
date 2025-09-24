# File Globbing

## Matching Paths with [ ]
Globbing happens on a path basis, so you can expand entire paths with your globbed arguments. For example:

```bash
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: /home/hacker/file_[ab]
Look: /home/hacker/file_a /home/hacker/file_b
```

### Objective 
We've placed a bunch of files in /challenge/files. Starting from your home directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files!

### Solve
**Flag:** `pwn.college{gpnF7WJDLCZk0uVJj6eFzbxoSzl.dRjM4QDLygjN0czW}`

-> In this challenge, as is mentioned, there are a bunch of files in the */challenge/files* directory. So the first thing I did was to change my directory to */challenge/files* and list all the files present there.  
-> Then I came back to the home directory and ran the */challenge/run* command with the absolute path to the target files as an argument. Since the only files required were a,b,s and h, I made use of the [ ] to glob them together.

```bash
hacker@globbing~matching-paths-with-:~$ cd /challenge
hacker@globbing~matching-paths-with-:/challenge$ ls
DESCRIPTION.md  files  run
hacker@globbing~matching-paths-with-:/challenge$ cd files
hacker@globbing~matching-paths-with-:/challenge/files$ ls
file_a  file_d  file_g  file_j  file_m  file_p  file_s  file_v  file_y
file_b  file_e  file_h  file_k  file_n  file_q  file_t  file_w  file_z
file_c  file_f  file_i  file_l  file_o  file_r  file_u  file_x
hacker@globbing~matching-paths-with-:/challenge/files$ cd
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file
_[absh]
You got it! Here is your flag!
pwn.college{gpnF7WJDLCZk0uVJj6eFzbxoSzl.dRjM4QDLygjN0czW}
```

### New Learnings
1. The globbing patterns can also be used on absolute paths along with files and directories names.  
