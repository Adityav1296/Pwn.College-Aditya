# Digesting Documentation 

## Searching Manuals
You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!

### Objective
Find the option that will give you the flag by reading the challenge man page.

### Solve
**Flag:** `pwn.college{02N-3u7HD8Yzux1KcsX65zxenm3.dVTM4QDLygjN0czW}`

-> In this challenge, the first thing I did was to use *man* command with *challenge* as the argument to understand how the *challenge* command works.  
-> Then I used '/' to find the option that will give me the flag. Using 'n' to traverse to the next instance of the keyword flag I found the correct option to get the flag.  
-> After that I ran the */challenge/challenge* command with some of its available options to test them out and with the one that gave me the required flag.

```bash
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --version
Initializing...
I'm exactly the version I need to be!
hacker@man~searching-manuals:~$ /challenge/challenge --fortune
Initializing...
A committee takes root and grows, it flowers, wilts and dies, scattering the
seed from which other committees will bloom.
                -- Parkinson
hacker@man~searching-manuals:~$ /challenge/challenge --sfimm
Initializing...
Correct usage! Your flag: pwn.college{02N-3u7HD8Yzux1KcsX65zxenm3.dVTM4QDLygjN0czW}
```

### New Learning
1. The *man* command opens up the manual for any particular command given to it as argument but the manual itself can sometimes contain a lot of information that is not required by us at that moment. Therefore to search for the required information or option for the command, we use '/ keyword' to search the manual page for the keyword from the top and '? keyword' to search the manual page for the keyword from the bottom.  
2. Navigation from one instance of the keyword to another can be done by using 'n' to go to the next instance and 'N' to go to the previous instance while the normal scrolling can be done using the arrow keys.