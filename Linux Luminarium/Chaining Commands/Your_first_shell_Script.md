# Chaining Commands

## Your first Shell Script
You can put these commands in a file, called a shell script, and run them by executing the file! For example, consider our semicolon technique:

```bash
hacker@dojo:~$ echo COLLEGE > pwn; cat pwn
COLLEGE
hacker@dojo:~$
```

We can create a shell script called pwn.sh (by convention, shell scripts are frequently named with a sh suffix). And then we can execute by passing it as an argument to a new instance of our shell (bash)! When a shell is invoked like this, rather than taking commands from the user, it reads commands from the file.

```bash
hacker@dojo:~$ ls
hacker@dojo:~$ bash pwn.sh
COLLEGE
hacker@dojo:~$ ls
pwn
hacker@dojo:~$
```

### Objective
Run /challenge/pwn and then /challenge/college, but this time in a shell script called x.sh, then run it with bash!

### Solve
**Flag:** `pwn.college{suiU9g90rmAk9wrG1Zxj5HHbBTn.dFzN4QDLygjN0czW}`

- The first thing I did was to create the x.sh file. Then I used `ls -l` command to list all its permission. Since it did not have any execution permission, I added the exection permission to the user.
- Then I used the `nano x.sh` command to open the file and write the commands to be executed in it. 
- Finally at the end, I used the `bash` command with the file as its argument to execute the script and get the flag.

```
hacker@chaining~your-first-shell-script:~$ touch x.sh
hacker@chaining~your-first-shell-script:~$ ls -l x.sh
-rw-r--r-- 1 hacker hacker 0 Sep 26 16:59 x.sh
hacker@chaining~your-first-shell-script:~$ chmod u+x x.sh
hacker@chaining~your-first-shell-script:~$ ls -l x.sh
-rwxr--r-- 1 hacker hacker 0 Sep 26 16:59 x.sh
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{suiU9g90rmAk9wrG1Zxj5HHbBTn.dFzN4QDLygjN0czW}
```

### New Learnings
1. We can use shell scripts to write entire codes in them and execute them in a single line by executing the script. This way we won't have to write the code again and again and we can reuse the script whenever we want to execute the code.
2. We use the `nano` command to open the text editor used in the terminal and provide the script name as an argument to it so that we can write into that script.
3. To execute the script, we use the `bash script_name` command.
4. We might need to add the executable permission to the script file sometimes before we can run it.

### Reference
1. [GeeksforGeeks:How to create a shell script in Linux](https://www.geeksforgeeks.org/linux-unix/how-to-create-a-shell-script-in-linux/)
