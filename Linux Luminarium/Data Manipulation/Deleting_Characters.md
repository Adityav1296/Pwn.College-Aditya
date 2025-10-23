# Data Manipulation

## Deleting Characters
tr can also translate characters to nothing (i.e., delete them). This is done via a -d flag and an argument of what characters to delete:

```bash
hacker@dojo:~$ echo PAWN | tr -d A
PWN
hacker@dojo:~$
```

### Objective
I'll intersperse some decoy characters (specifically: ^ and %) among the flag characters. Use tr -d to remove them!

### Solve
**Flag:** `pwn.college{oEbz2V2S0WsTG0IjWVOwZF0Q2zS.QX0ETM3EDLygjN0czW}`

- In this challenge, I straightaway used the piping operator to pipe the output of */challenge/run* command and on the other side, I used *tr -d* command as specified. However, there are two way to pass arguments to the *tr -d* command :
  1. Directly pass the characters to be deleted : ^%
  2. Enclose the characters to be deleted in '^%'.


```bash
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^%
Your character-stuffed flag:
pwn.college{oEbz2V2S0WsTG0IjWVOwZF0Q2zS.QX0ETM3EDLygjN0czW}
hacker@data~deleting-characters:~$ /challenge/run | tr -d '^%'
Your character-stuffed flag:
pwn.college{oEbz2V2S0WsTG0IjWVOwZF0Q2zS.QX0ETM3EDLygjN0czW}
```

### New Learnings
1. *tr -d* command is used for deleting the characters specified to it as argument. We can give arguement to it in two ways :
    1. Directly pass the characters to be deleted.
    2. Enclose the characters to be deleted in ' '. This is a more secure way of passing the arguments to delete.

### References 
1. [GeeksforGeeks : tr command in Unix/Linux with examples](https://www.geeksforgeeks.org/linux-unix/tr-command-in-unix-linux-with-examples/)
