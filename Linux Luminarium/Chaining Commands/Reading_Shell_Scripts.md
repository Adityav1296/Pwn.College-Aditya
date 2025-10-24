# Chaining Commands

## Reading Shell Scripts
You're not the only one who writes shell scripts! They are very handy for doing simple "system-level" tasks, and are a common tool that developers and sysadmins reach for. In fact, a surprising fraction of the programs on a typical Linux machine are shell scripts.

### Objective
In this level, we will learn to read shell scripts. /challenge/run is a shell script that requires you to put in a secret password, but that password is hardcoded into the script iself! Read the script (using, say, cat), figure out the password, and get the flag!

### Solve
**Flag:** `pwn.college{krKeUTvWlZZ-VraAU9C1Mo7cPmj.QXyADO4EDLygjN0czW}`

- The first thing I did was to change my directory to /challenge. There I listed the files present in it along with their permissions using the `ls -l` command.
- Then I used the `cat` command to read the shell script 'run'. There I found the info that the secrect password to be passed to the script should be 'hack the PLANET'.
- Since the script is reading from stdin, even if I had input using the normal way of passing the argument to the script, it would not give me the correct solution. Therefore, I echoed the password and piped it to the script. From there, the script read the password and I obtained the flag.

```bash
hacker@chaining~reading-shell-scripts:~$ cd /challenge
hacker@chaining~reading-shell-scripts:/challenge$ ls -l
total 8
-rwsr-xr-x 1 root root 1034 Aug 24 19:04 DESCRIPTION.md
-rwsr-xr-x 1 root root  198 Aug 24 19:04 run
hacker@chaining~reading-shell-scripts:/challenge$ cat ./run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:/challenge$ echo "hack the PLANET" | ./run
CORRECT! Your flag:
pwn.college{krKeUTvWlZZ-VraAU9C1Mo7cPmj.QXyADO4EDLygjN0czW}
```

### New Learnings
1. The 'read variable_name' line in the script is used to take and read the input directly form stdin. As a result, the usual command-line arguments like '$1' won't be useful in the script at places where the 'variable_name' is being used.
2. In order to pass the values to the script as stdin, we can pipe them in to the script or we can run the script interactively as follows :

```bash
hacker@chaining~reading-shell-scripts:/challenge$ ./run
hack the PLANET
CORRECT! Your flag:
pwn.college{krKeUTvWlZZ-VraAU9C1Mo7cPmj.QXyADO4EDLygjN0czW}
```

The script will wait for us to type in the value for the variable taking input from the stdin.
