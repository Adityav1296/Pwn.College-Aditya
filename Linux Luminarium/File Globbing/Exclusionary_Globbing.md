# File Globbing

## Expulsionary Globs
Sometimes, you want to filter out files in a glob! Luckily, [] helps you do just this. If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed. For example:

```bash
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[!ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[^ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
```

### Objective 
Go forth to /challenge/files and run /challenge/run with all files that don't start with p, w, or n!

### Solve
**Flag:** `pwn.college{E-h5hu4FmwaXcxML5ycPN7V15Mj.dZjM4QDLygjN0czW}`

-> In this challenge, after changing my directory to */challenge/files*, I initially listed the files present inside the directory.  
-> Then I just used `[^pwn]*` as argument to */challenge/run* in order to include all those file that do not begin with the letters 'p','w' and 'n'.

```bash
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ ls
amazing      fantastic   kind        pwning     uplifting   zesty
beautiful    great       laughing    queenly    victorious
challenging  happy       magical     radiant    wonderful
delightful   incredible  nice        splendid   xenial
educational  jovial      optimistic  thrilling  youthful
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{E-h5hu4FmwaXcxML5ycPN7V15Mj.dZjM4QDLygjN0czW}
hacker@globbing~exclusionary-globbing:/challenge/files$ file [!pwn]*
amazing:     setuid, empty
beautiful:   setuid, empty
challenging: setuid, empty
delightful:  setuid, empty
educational: setuid, empty
fantastic:   setuid, empty
great:       setuid, empty
happy:       setuid, empty
incredible:  setuid, empty
jovial:      setuid, empty
kind:        setuid, empty
laughing:    setuid, empty
magical:     setuid, empty
optimistic:  setuid, empty
queenly:     setuid, empty
radiant:     setuid, empty
splendid:    setuid, empty
thrilling:   setuid, empty
uplifting:   setuid, empty
victorious:  setuid, empty
xenial:      setuid, empty
youthful:    setuid, empty
zesty:       setuid, empty
```

### New Learnings
1. Just like we can limit the number of characters to look for in the file or directory names by using [], we can also use these [] with either '^' or '!' symbol in the beginning inside the [] to exclude a particular set of characters from the search.  