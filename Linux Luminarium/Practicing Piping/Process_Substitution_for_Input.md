# Practicing Piping

## Process Substitution for Input
Sometimes you need to compare the output of two commands rather than two files. You might think to save each output to a file first and then compare them using *diff*. 

But there's a more elegant way! Linux follows the philosophy that "everything is a file". The shell follows this philosophy, allowing you to, for example, use any utility that takes file arguments on the command line and hook it up to the output of programs.

Interestingly, we can go further, and hook input and output of programs to arguments of commands. This is done using Process Substitution. For reading from a command (input process substitution), use <(command). When you write <(command), bash will run the command and hook up its output to a temporary file that it will create. This isn't a real file, of course, it's what's called a named pipe, in that it has a file name:

```bash
hacker@dojo:~$ echo <(echo hi)
/dev/fd/63
hacker@dojo:~$
```

bash replaced <(echo hi) with the path of the named pipe file that's hooked up to the command's output! While the command is running, reading from this file will read data from the standard output of the command. Of course, you can specify this multiple times:

```bash
hacker@dojo:~$ echo <(echo pwn) <(echo college)
/dev/fd/63 /dev/fd/64
hacker@dojo:~$ cat <(echo pwn) <(echo college)
pwn
college
hacker@dojo:~$
```

### Objective 
In this challenge, you'll diff two sets of command outputs: /challenge/print_decoys, which will print a bunch of decoy flags, and /challenge/print_decoys_and_flag which will print those same decoys plus the real flag.

Use process substitution with diff to compare the outputs of these two programs and find your flag!

### Solve
**Flag:** `pwn.college{cZ12KyIkMHpItSYbJBdjg0cSq9T.QX2AzM4EDLygjN0czW}`

- From the challenge description and the obejctive, I understood that the inputs to the commands can be substitued by the outputs of some other commands and processes. These new inputs are stored in temporary files called named pipe files and hence we can perform all file commands on them.
- Therefore, I used the *diff* command and used the outputs of the */challenge/print_decoys* and */challenge/print_decoys_and_flag* commands as inputs to it. Since the outputs of the two commands get stored as named pipe files, we can perform the *diff* command on them to find the hidden flag.

```bash
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
39a40
> pwn.college{cZ12KyIkMHpItSYbJBdjg0cSq9T.QX2AzM4EDLygjN0czW}
```

### New Learnings
1. I understood that the inputs to the commands can be substitued by the outputs of some other commands and processes. These new inputs are stored in temporary files called named pipe files and hence we can perform all file commands on them.
2. Input process subsitution is written in *<(command)* format.
3. We can find the names of those files by using the *echo* comamnd since the inputs it will receive by substituting the inputs by the outputs of some other processes are the names of the named pipe files. Example :

```bash
hacker@piping~process-substitution-for-input:~$ echo <(/challenge/print_deco
ys) <(/challenge/print_decoys_and_flag)
/dev/fd/63 /dev/fd/62
```