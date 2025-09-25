# Data Manipulation

## Translating Characters
One of the purposes of piping data is to modify it. Many Linux commands will help you modify data in really cool ways. One of these is tr, which translates characters it receives over standard input and prints them to standard output.

In its most basic usage, tr translates the character provided in its first argument to the character provided in its second argument:

```bash
hacker@dojo:~$ echo OWN | tr O P
PWN
hacker@dojo:~$
```

It can also handle multiple characters, with the characters in different positions of the first argument replaced with associated characters in the second argument.

```bash
hacker@dojo:~$ echo PWM.COLLAGE | tr MA NE
PWN.COLLEGE
hacker@dojo:~$
```

### Objective
In this level, /challenge/run will print the flag but will swap the casing of all characters (e.g., A will become a and vice-versa). Can you undo it with tr and get the flag?

### Solve
**Flag:** `pwn.college{84G3ps5B2cuG4CIC87fNYDkGc3b.QXzETM3EDLygjN0czW}`

- In this challenge, it was clear that we need to pipe the output of */challenge/run* command. The main thing was how to change the case of the characters in the output.
- First I thought of writing all the characters alternatively in upper case and lower case as argument to *tr* and then write them in opposite order as the second argument i.e `'AaBbCcDd....' 'aAbBcCdD....'`. But I realized that it will be too long of an argument to give. Moreover, it will only swap one occurance of the characters not all of them.
- Finally I looked up a the different ways to use the *tr* command and found a case that suits this challenge.
- By combining the two ways in which that case can be applied, I managed to switch the case of all the characters in the output file and got the flag.

```bash
hacker@data~translating-characters:~$ /challenge/run | tr '[:upper:]' '[:lower:]'
your case-swapped flag:
pwn.college{84g3ps5b2cug4cic87fnydkgc3b.qxzetm3edlygjn0czw}
hacker@data~translating-characters:~$ /challenge/run | tr '[:lower:]' '[:upper:]'
YOUR CASE-SWAPPED FLAG:
PWN.COLLEGE{84G3PS5B2CUG4CIC87FNYDKGC3B.QXZETM3EDLYGJN0CZW}
hacker@data~translating-characters:~$ /challenge/run | tr '[:upper:][:lower:]' '[:lower:][:upper:]'
yOUR CASE-SWAPPED FLAG:
pwn.college{84G3ps5B2cuG4CIC87fNYDkGc3b.QXzETM3EDLygjN0czW}
```

### New Learnings
1. *tr* command is used for translating or deleting characters. It supports a range of transformations including uppercase to lowercase, squeezing repeating characters, deleting specific characters, and basic find and replace.


### References 
1. [GeeksforGeeks : tr command in Unix/Linux with examples](https://www.geeksforgeeks.org/linux-unix/tr-command-in-unix-linux-with-examples/)
