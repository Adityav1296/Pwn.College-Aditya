# Digesting Documentation 

## Helpful Programs
Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /?

### Objective
In this level, you will practice reading a program's documentation with --help. Try it out!

### Solve
**Flag:** `pwn.college{EZVn3bex5oCDW6U550oIjGs5zDM.ddjM4QDLygjN0czW}`

-> In this challenge, I simply started with */challenge/challenge --help* to look for any information available about it.  
-> There I got the required steps I need to do to get the flag. After performing them, I was able to obtain the flag as below.

```bash
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v]   [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to
                        give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 356
hacker@man~helpful-programs:~$ /challenge/challenge -g 356
Correct usage! Your flag: pwn.college{EZVn3bex5oCDW6U550oIjGs5zDM.ddjM4QDLygjN0czW}
hacker@man~helpful-programs:~$ /challenge/challenge --fortune
A meeting is an event at which the minutes are kept and the hours are lost.
```

### New Learning
1. Some commands might not have their manual pages but we can still find some information on them using the *--help* option after them. The information can include additional description about the command or some options that we can use along with the command.