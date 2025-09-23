# Comprehending Commands 

## Comparing Files
When looking for changes between similar files, eyeballing them might not be the most efficient approach! This is where the diff command becomes invaluable.

diff compares two files line by line and shows you exactly what's different between them. For example:

```
hacker@dojo:~$ cat file1
hello
world
hacker@dojo:~$ cat file2
hello
universe
hacker@dojo:~$ diff file1 file2
2c2
< world
---
> universe
```

The output tells us that line 2 changed (2c2), with world in the first file (<) being replaced by universe in the second file (>).

Sometimes, when new lines are added, you'll see something like:

```
hacker@dojo:~$ cat old
pwn
hacker@dojo:~$ cat new
pwn
college
hacker@dojo:~$ diff old new
1a2
> college
```

### Objective
Now for your challenge! There are two files in /challenge:

- /challenge/decoys_only.txt contains 100 fake flags
- /challenge/decoys_and_real.txt contains all 100 fake flags plus the one real flag

Use diff to find what's different between these files and get your flag!

### Solve
**Flag:** `pwn.college{IrWBOthHw2Z4ulJ_Surcu41JNLw.QXzAzM4EDLygjN0czW}`

-> In this challenge, I ran the *diff* command with the two absolute paths provided in the challenge to get the correct flag.  
-> Other than that I also ran the *grep -n "pwn.college" path* command with both the absolute paths to get the line numbers for content in both the files. From there also I confirmed that both the files are same till the 78th line. There is an additional line in */challenge/decoys_and_real.txt* at number 79. That's where the diff command also showed the correct flag being found. 

```bash
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
78a79
> pwn.college{IrWBOthHw2Z4ulJ_Surcu41JNLw.QXzAzM4EDLygjN0czW}
```

### New Learning
1. *diff* command compares 2 files line by line, prints only their differences and tells is what we need to change in file 1 to make it identical to file 2.  
2. *diff* command has the following 3 types of outputs :  
   1. N1aN2 : After line N1 in file 1, add line N2 of file 2.  
   2. N4dN3 : In file 1, delete line N4 to make it same as file 2.  
   3. N6cN6 : Line N6 in file 1 is different from line N6 in file 2. Therefore line N6 in file 1 must be changed to line N6 of file 2.  
3. It displays all the differences between the two files even when there are multiple of them. 
4. It doesn't make any change to any of the files itself.

### References
1. Chatgpt for additional information on *diff* command.
