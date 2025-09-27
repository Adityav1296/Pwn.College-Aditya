# Pondering PATH

## Finding Commands
When you type the name of a command, something inside one of the many directories listed in your $PATH variable is what actually gets executed (of course, unless the command is a builtin!). But which file, precisely? You can find out with the aptly-named which command:

```bash
hacker@dojo:~$ which cat
/bin/cat
hacker@dojo:~$ /bin/cat /flag
YEAH
hacker@dojo:~$
```

Mirroring what the shell does when searching for commands, which looks at each directory in $PATH in order and prints the first file it finds whose name matches the argument you passed.

### Objective
In this challenge, we added a win command somewhere in your $PATH, but it won't give you the flag. Instead, it's in the same directory as a flag file that we made readable by you! You must find win (with the which command), and cat the flag out of that directory!

### Solve
**Flag:** `pwn.college{oIlZFeIaBhjwwi2VwC6qYzweiYB.QX3MTM3EDLygjN0czW}`

- First I ran the `which` command with some basic commands to look up their locations. After that, I ran it with the 'win' command as its argument to find the directory of the 'win' command.
- As is mentioned in the objective, the flag lies in the same directory as win. Therefore, I changed my directory to the directory containing the flag and used `cat` to read the flag.

```bash
hacker@path~finding-commands:~$ which file
/run/dojo/bin/file
hacker@path~finding-commands:~$ which sudo
/run/dojo/bin/sudo
hacker@path~finding-commands:/challenge/paths/9059$ which which
/run/dojo/bin/which
hacker@path~finding-commands:~$ which win
/challenge/paths/9059/win
hacker@path~finding-commands:~$ cd /challenge/paths/9059
hacker@path~finding-commands:/challenge/paths/9059$ ls
flag  win
hacker@path~finding-commands:/challenge/paths/9059$ cat flag
pwn.college{oIlZFeIaBhjwwi2VwC6qYzweiYB.QX3MTM3EDLygjN0czW}
```

### New Learnings
1. We can use `which command_name` command in order to find the directory where the argument command is stored.

### References
1. [GeeksforGeeks : Setting $PATH](https://www.geeksforgeeks.org/linux-unix/how-to-set-path-permanantly-in-linux/)