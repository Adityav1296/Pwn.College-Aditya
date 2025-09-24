# File Globbing

## Matching with ?
When it encounters a ? character in any argument, the shell will treat it as a single-character wildcard. This works like *, but only matches one character. For example:

```bash
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_cc
hacker@dojo:~$ ls
file_a	file_b	file_cc
hacker@dojo:~$ echo Look: file_?
Look: file_a file_b
hacker@dojo:~$ echo Look: file_??
Look: file_cc
```

### Objective 
Starting from your home directory, change your directory to /challenge, but use the ? character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag!

### Solve
**Flag:** `pwn.college{sdlxHqrj9l72fsaYWI7nH4lEaCA.dJjM4QDLygjN0czW}`

-> This was a direct challenge where I just had to use '?' in place of 'c' and 'l' when passing */challenge* as argument to *cd* command.  

```bash
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{sdlxHqrj9l72fsaYWI7nH4lEaCA.dJjM4QDLygjN0czW}
```

### New Learnings
1. The ? symbol can replace any of the characters in the file name. As a result, the shell tries to replace the ? symbol with any files that match the pattern given before or after it.  
2. Similar to using *, by using ? we can search up multiple files having the same pattern by a single command rather than searching them one by one.  
3. We can also use * symbol to perform its function with the directories as well, just like how we did in this challenge.  
4. The only difference between * and ? here is that ? can only replace one character while * can also be used to replace a bunch of characters in the file or directory name. As a result, the ? is used when we need strict position control and want to match only a fixed number of characters. Otherwise we can use * for flexibility.