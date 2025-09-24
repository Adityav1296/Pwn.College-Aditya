# File Globbing

## Mixing Globs
Now, let's put the previous levels together!

### Objective 
We put a few happy, but diversely-named files in /challenge/files. Go cd there and, using the globbing you've learned, write a single, short (6 characters or less) glob that (when passed as an argument to /challenge/run) will match the files "challenging", "educational", and "pwning"!

### Solve
**Flag:** `pwn.college{8o5fcAKGFcRjasYbLF4ZyGXKkn2.dVjM4QDLygjN0czW}`

-> In this challenge, after changing my directory to */challenge/files*, I initially listed the files present inside the directory.  
-> Then initially, I found that 'in' are two common characters in the files that we need to search. Therefore, I executed the */challenge/run* command with `*[in]*` as an argument. But along with the required files, a number of other files also got listed as they also contained 'i' and 'n' in their names.  
-> Then I again tried by using `*[i?]*` as an argument to see if it works but this also displayed extra files.  
-> Then I stopped and observed the names of the files that I had listed earlier. From there I found that only the required files were beginning with the letters 'p','e' and 'c'. That's when it all clicked together.  
-> Therefore I put the 3 letters in [] like [pec] to look only for files that start with these letters and added '*' at the end so that it expands to match their entire names.

```bash
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ ls
amazing      fantastic   kind        pwning     uplifting   zesty
beautiful    great       laughing    queenly    victorious
challenging  happy       magical     radiant    wonderful
delightful   incredible  nice        splendid   xenial
educational  jovial      optimistic  thrilling  youthful
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run *[in]*
Your expansion did not expand to the requested files (challenging, educational,
pwning). Instead, it expanded to:
amazing beautiful challenging delightful educational fantastic incredible jovial kind laughing magical nice optimistic pwning queenly radiant splendid thrilling uplifting victorious wonderful xenial
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run *[i?]*
Your expansion did not expand to the requested files (challenging, educational,
pwning). Instead, it expanded to:
amazing beautiful challenging delightful educational fantastic incredible jovial kind laughing magical nice optimistic pwning radiant splendid thrilling uplifting victorious xenial
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [pec]*
You got it! Here is your flag!
pwn.college{8o5fcAKGFcRjasYbLF4ZyGXKkn2.dVjM4QDLygjN0czW}
```

### New Learnings
1. Earlier we used mulitple glob patterns together but now I got to know that we can use different kinds of glob patterns together as well to make up the desired arguments that suits our requirements.  