# Shell Variables

## Setting Variables
You can write values to variables. This is done, as with many other languages, using =. To set variable VAR to value 1337, you would use:

```bash
hacker@dojo:~$ VAR=1337
```

Note that there are no spaces around the =! If you put spaces (e.g., VAR = 1337), the shell won't recognize a variable assignment and will, instead, try to run the VAR command (which does not exist).

Also note that this uses VAR and not $VAR: the $ is only prepended to access variables. In shell terms, this prepending of $ triggers what is called variable expansion, and is, surprisingly, the source of many potential vulnerabilities.

### Objective 
To solve this level, you must set the PWN variable to the value COLLEGE. Be careful: both the names and values of variables are case-sensitive! PWN is not the same as pwn and COLLEGE is not the same as College.

### Solve
**Flag:** `pwn.college{YRbaQYl50Jpw0VNSURBGL4ByDCz.dlTN1QDLygjN0czW}`

- In this challenge, I just assigned the value COLLEGE to the variable PWN by using the method given in the challenge description and got the flag.
- Just to check, I also executed `echo $PWN` and got COLLEGE as output along with flag.

```bash
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{YRbaQYl50Jpw0VNSURBGL4ByDCz.dlTN1QDLygjN0czW}
hacker@variables~setting-variables:~$ echo $PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{YRbaQYl50Jpw0VNSURBGL4ByDCz.dlTN1QDLygjN0czW}
```

### New Learnings
1. If we can print the variables, we can also assign values to them. This can be easily done by using '=' operator. But keep in mind that we cannot give any space between the variable, = operator and the value being assigned.