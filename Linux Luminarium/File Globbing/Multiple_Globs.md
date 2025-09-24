# File Globbing

## Multiple Globs
So far, you've specified one glob at a time, but you can do more! Bash supports the expansion of multiple globs in a single word. For example:

```bash
hacker@dojo:~$ cat /*fl*
pwn.college{YEAH}
hacker@dojo:~$
```

What happens above is that the shell looks for all files in / that start with anything (including nothing), then have an f and an l, and end in anything (including ag, which makes flag).

### Objective 
We put a few happy, but diversely-named files in /challenge/files. Go cd there and run /challenge/run, providing a single argument: a short (3 characters or less) globbed word with two * globs in it that covers every word that contains the letter p.

### Solve
**Flag:** `pwn.college{EgywhFQvtc7_bgiLGcjUYmsUDr3.QXycTO2EDLygjN0czW}`

-> In this challenge, after changing my directory to */challenge/files*, I initially listed the files present inside the directory.  
-> Then, as specified by the challenge, I provide the `*p*` argument to */challenge/run* in order to cover all the files that have the letter 'p' in them. I also used the *file* command to list those particular files.

```bash
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ ls
amazing      fantastic   kind        pwning     uplifting   zesty
beautiful    great       laughing    queenly    victorious
challenging  happy       magical     radiant    wonderful
delightful   incredible  nice        splendid   xenial
educational  jovial      optimistic  thrilling  youthful
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{EgywhFQvtc7_bgiLGcjUYmsUDr3.QXycTO2EDLygjN0czW}
hacker@globbing~multiple-globs:/challenge/files$ file *p*
happy:      setuid, empty
optimistic: setuid, empty
pwning:     setuid, empty
splendid:   setuid, empty
uplifting:  setuid, empty
```

### New Learnings
1. We can use multiple globbing patterns together. They are all expanded by the shell as usual without any hindrance.   