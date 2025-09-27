# Chaining Commands

## Redirecting Script Output
As far as the shell is concerned, your script is just another command. That means you can redirect its input and output. For example, you can write it to a file:

```bash
hacker@dojo:~$ cat script.sh
echo PWN
echo COLLEGE
hacker@dojo:~$ bash script.sh > output
hacker@dojo:~$ cat output
PWN
COLLEGE
hacker@dojo:~$
```

### Objective
In this level, we will practice piping (|) from your script to another program. Like before, you need to create a script that calls the /challenge/pwn command followed by the /challenge/college command, and pipe the output of the script into a single invocation of the /challenge/solve command!

### Solve
**Flag:** `pwn.college{stqYcyft6FbSmdA4DnAsb0PmGw_.dhTM5QDLygjN0czW}`

- The first thing I did was to create the x.sh file. Then I used `ls -l` command to list all its permission. Since it did not have any execution permission, I added the exection permission to the user.
- Then I used the `nano x.sh` command to open the file and write the commands to be executed in it. 
- Finally at the end, I used the `bash` command with the file as its argument to execute the script and piped its output using the pipe operator to the `/challenge/solve` command.

```bash
hacker@chaining~redirecting-script-output:~$ touch x.sh
hacker@chaining~redirecting-script-output:~$ ls -l x.sh
-rw-r--r-- 1 hacker hacker 0 Sep 26 16:59 x.sh
hacker@chaining~redirecting-script-output:~$ chmod u+x x.sh
hacker@chaining~redirecting-script-output:~$ ls -l x.sh
-rwxr--r-- 1 hacker hacker 0 Sep 26 16:59 x.sh
hacker@chaining~redirecting-script-output:~$ nano x.sh
hacker@chaining~redirecting-script-output:~$ cat x.sh
/challenge/pwn; /challenge/college
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{stqYcyft6FbSmdA4DnAsb0PmGw_.dhTM5QDLygjN0czW}
```

### New Learnings
1. For the shell, the script is like a single command. Therefore the output of the script can be redirected using the piping operator just like the other commands.
2. All of the various redirection methods work: > for stdout, 2> for stderr, < for stdin, >> and 2>> for append-mode redirection, >& for redirecting to other file descriptors.