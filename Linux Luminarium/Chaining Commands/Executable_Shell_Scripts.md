# Chaining Commands

## Executable Shell Scripts
When you invoke bash script.sh, you are, of course launching the bash command with the script.sh argument. This tells bash to read its commands from script.sh instead of standard input, and thus your shell script is executed.

It turns out that you can avoid the need to manually invoke bash. If your shell script file is executable, you can simply invoke it via its relative or absolute path!

### Objective
Make a shellscript that will invoke /challenge/solve, make it executable, and run it without explicitly invoking bash!

### Solve
**Flag:** `pwn.college{kLZFUv3pN9AXUPNyfO0-V9vQXRU.dRzNyUDLygjN0czW}`

- The first thing I did was to create the x.sh file. Then I used `ls -l` command to list all its permission. Since it did not have any execution permission, I added the exection permission to the user.
- Then I used the `nano x.sh` command to open the file and write the commands to be executed in it. 
- Finally at the end, I simply executed the script by invoking it through a relative path and got the flag.

```bash
hacker@chaining~redirecting-script-output:~$ touch x.sh
hacker@chaining~redirecting-script-output:~$ ls -l x.sh
-rw-r--r-- 1 hacker hacker 0 Sep 26 16:59 x.sh
hacker@chaining~redirecting-script-output:~$ chmod u+x x.sh
hacker@chaining~redirecting-script-output:~$ ls -l x.sh
-rwxr--r-- 1 hacker hacker 0 Sep 26 16:59 x.sh
hacker@chaining~redirecting-script-output:~$ nano x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{kLZFUv3pN9AXUPNyfO0-V9vQXRU.dRzNyUDLygjN0czW}
```

### New Learnings
1. When we provide the executable permission to the script, we don't need to invoke it through the `bash` command. We can simply call upon it through an absolute or relative path.