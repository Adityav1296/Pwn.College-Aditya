# Practicing Piping

## Writing to Multiple Programs 
You can also use process substitution for writing to commands! 

You can duplicate data to two files with tee and you've used tee to duplicate data to a file and a command. But what about duplicating to two commands? As tee says in its manpage, it's designed to write to files and to standard output.

Bash can make commands look like files using process substitution! For writing to a command (output process substitution), use >(command). If you write an argument of >(rev), bash will run the rev command but hook up its input to a temporary named pipe file. When commands write to this file, the data goes to the standard input of the command:

```bash
hacker@dojo:~$ echo HACK | rev
KCAH
hacker@dojo:~$ echo HACK | tee >(rev)
HACK
KCAH
```

Above, the following sequence of events took place:

   1. bash started up the rev command, hooking a named pipe (presumably /dev/fd/63) to rev's standard input
   2. bash started up the tee command, hooking a pipe to its standard input, and replacing the first argument to tee with /dev/fd/63. tee never even saw the argument >(rev); the shell substituted it before launching tee
   3. bash used the echo builtin to print HACK into tee's standard input
   4. tee read HACK, wrote it to standard output, and then wrote it to /dev/fd/63 (which is connected to rev's stdin)
   5. rev read HACK from its standard input, reversed it, and wrote KCAH to standard output

### Objective 
In this challenge, we have /challenge/hack, /challenge/the, and /challenge/planet. Run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands!

### Solve
**Flag:** `pwn.college{EXT9vQ2hRu0brDlCUojyUM11cmF.dBDO0UDLygjN0czW}`

- From the challenge description and the obejctive, I understood that the outputs of the commands can be used as inputs by some other commands and processes. The standard inputs of those processes are linked to a named pipe file. 
- Initially I tried to use *echo* command along with the */challenge/hack* command but soon realized that it was wrong because in this particular case, */challenge/hack* prints the output itself without any need for *echo*.
- Therefore I removed *echo*. Now with >(/challenge/the), >(/challenge/planet) as arguments to the *tee* command, these two are basically named pipe files whose outputs are connected to the stdin of these commands. As a result we are able to redirect the output correctly and obtain the flag. 

```bash
hacker@piping~writing-to-multiple-programs:~$ echo /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
/challenge/hack
Are you sure you're properly redirecting input into '/challenge/planet'?
Are you sure you're properly redirecting input into '/challenge/the'?
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
2990212961619330468
Congratulations, you have duplicated data into the input of two programs! Here is your flag:
pwn.college{EXT9vQ2hRu0brDlCUojyUM11cmF.dBDO0UDLygjN0czW}
```

### New Learnings
1. I understood that the outputs of the commands can be used as inputs by some other commands and processes. The standard inputs of those processes are linked to a named pipe file.
2. Now when written in this form : >(command1), >(command2) as arguments to another command, these two are basically named pipe files whose outputs are connected to the stdin of command1 and command2.
3. In this way, we can perform reading functions by using Process_Substituion_for_Input and perform writing function by using Process_Substituion_for_Output.