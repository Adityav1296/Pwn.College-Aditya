# Comprehending Commands 

## Cat : Not the pet, But the Command!
One of the most critical Linux commands is cat. cat is most often used for reading out files, like so:

```
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:
```

cat will concatenate (hence the name) multiple files if provided multiple arguments. For example:

```
hacker@dojo:~$ cat myfile
This is my file!
hacker@dojo:~$ cat yourfile
This is your file!
hacker@dojo:~$ cat myfile yourfile
This is my file!
This is your file!
hacker@dojo:~$ cat myfile yourfile myfile
This is my file!
This is your file!
This is my file!
```

Finally, if you give no arguments at all, cat will read from the terminal input and output it. 

### Objective
In this challenge, the flag will be copied to the flag file in your home directory (where your shell starts). Go read it with cat!

### Solve
**Flag:** `pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}`

-> In this challenge, I directly executed the *cat* command with *flag* as the argument to get the command.  
-> I also found that there are multiple ways to do this same task : 
  - First I put */flag* as the argument and got the flag.
  - Second, I changed my directory to root(/) and then ran *cat flag* and again got the flag.

```bash
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
hacker@commands~cat-not-the-pet-but-the-command:~$ cat /flag
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
hacker@commands~cat-not-the-pet-but-the-command:~$ cd /
hacker@commands~cat-not-the-pet-but-the-command:/$ cat flag
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
```

### New Learning
1. Cat command reads the content of the target file given as the argument onto the terminal.
2. It can concatenate the contents of multiple files together when more than one arguments are given.
3. Useful for small, text-based files but not good for huge files. 
