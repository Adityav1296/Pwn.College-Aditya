# File Globbing

## Matching with [ ]
The square brackets are, essentially, a limited form of ?, in that instead of matching any character, [ ] is a wildcard for some subset of potential characters, specified within the brackets. For example, [pwn] will match the character p, w, or n. For example:

```bash
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
```

### Objective 
We've placed a bunch of files in /challenge/files. Change your working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h!

### Solve
**Flag:** `pwn.college{U6-gYzQfSC0S_ny-J3LgghbBKs9.dNjM4QDLygjN0czW}`

-> This was a direct challenge where I used the square brackets containing the required letters to look for in the file names. Placing the square brackets at the correct position I was able to get the correct expansion to the requested files and obtained the flag as well.

```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ ls
file_a  file_d  file_g  file_j  file_m  file_p  file_s  file_v  file_y
file_b  file_e  file_h  file_k  file_n  file_q  file_t  file_w  file_z
file_c  file_f  file_i  file_l  file_o  file_r  file_u  file_x
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{U6-gYzQfSC0S_ny-J3LgghbBKs9.dNjM4QDLygjN0czW}
```

### New Learnings
1. Similar to ? symbol being used for file globbing, the [ ] also act as wildcard for a single position only.  
2. Just like with ? symbol, it is necessary to place the [ ] at the correct position in the file or directory name when file globbing.  
3. [] make the search area even less as compared to ? since we can specify the particular characters to look for or not look for when file globbing.
