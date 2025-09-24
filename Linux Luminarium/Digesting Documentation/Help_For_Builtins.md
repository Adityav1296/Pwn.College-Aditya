# Digesting Documentation 

## Help for Builtins
Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. You can get a list of shell builtins by running the builtin help, as so: 

```
hacker@dojo:~$ help
```

You can get help on a specific one by passing it to the help builtin. Let's look at a builtin that we've already used earlier, cd!

```
hacker@dojo:~$ help cd
cd: cd [-L|[-P [-e]] [-@]] [dir]
    Change the shell working directory.
    
    Change the current directory to DIR.  The default DIR is the value of the
    HOME shell variable.
...
```

### Objective
In this challenge, we'll practice using help to look up help for builtins. This challenge's challenge command is a shell builtin, rather than a program. Like before, you need to lookup its help to figure out the secret value to pass to it!

### Solve
**Flag:** `pwn.college{Aw2QTdGT-tkgwKX9yUvkpWz1cyN.dRTM5QDLygjN0czW}`

-> In this challenge, I first ran the *help* builtin command on *help* itself to look up its description.  
-> Then I used the *help* builtin command again with *challenge* as an argument/pattern to get information about how to use it. From there, I found the secret value needed for acquiring the flag. Using the correct option from the description along with the secret value, I then obtained the flag.

```bash
hacker@man~help-for-builtins:~$ help help
help: help [-dms] [pattern ...]
    Display information about builtin commands.

    Displays brief summaries of builtin commands.  If PATTERN is specified, gives detailed help on all commands matching PATTERN, otherwise the list of help topics is printed.

    Options:
      -d        output short description for each topic
      -m        display usage in pseudo-manpage format
      -s        output only a short usage synopsis for each topic matching
                PATTERN

    Arguments:
      PATTERN   Pattern specifying a help topic

    Exit Status:
    Returns success unless PATTERN is not found or an invalid option is given.
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value is "Aw2QTdGT".
hacker@man~help-for-builtins:~$ challenge --secret Aw2QTdGT
Correct! Here is your flag!
pwn.college{Aw2QTdGT-tkgwKX9yUvkpWz1cyN.dRTM5QDLygjN0czW}
```

### New Learning
1. *help* as a builtin command is different then the *--help* option even though both of them display the description and the way to use the target command passed to them.  
2. They both work with different sets of commands. The builtin *help* can only work with builtin shell commands and programs while *--help* works only with external commands that can implement it.