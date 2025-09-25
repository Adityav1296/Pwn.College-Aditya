# Shell Variables

## Exporting Variables
By default, variables that you set in a shell session are local to that shell process. That is, other commands you run won't inherit them. 

```bash
hacker@dojo:~$ VAR=1337
hacker@dojo:~$ echo "VAR is: $VAR"
VAR is: 1337
hacker@dojo:~$ sh
$ echo "VAR is: $VAR"
VAR is:
```

In the output above, the $ prompt is the prompt of sh, a minimal shell implementation that is invoked as a child of the main shell process. And it does not receive the VAR variable! You don't want your variables leaking to other programs you run unless it explicitly should. How do you mark that it should? You export your variables. When you export your variables, they are passed into the environment variables of child processes. 

```bash
hacker@dojo:~$ VAR=1337
hacker@dojo:~$ export VAR
hacker@dojo:~$ sh
$ echo "VAR is: $VAR"
VAR is: 1337
```

### Objective 
In this challenge, you must invoke /challenge/run with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported (e.g., not inherited by /challenge/run).

### Solve
**Flag:** `pwn.college{Qz7C-LLAd6D9yFgaSBmYL2_K8zU.dJjN1QDLygjN0czW}`

- In this challenge, first I set the value of variable COLLEGE to PWN.
- Then I directly exported the variable PWN with its value set to COLLEGE.
- Finally I launched a subshell using *sh* command and ran the */challenge/run* command with PWN as its argument.

```bash
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You have set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You have set the PWN variable to the proper value!
You have set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ sh
sh-5.2$ /challenge/run PWN
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great job! Here is your flag:
pwn.college{Qz7C-LLAd6D9yFgaSBmYL2_K8zU.dJjN1QDLygjN0czW}
sh-5.2$ exit
exit
You have set the PWN variable to the proper value!
You have set the COLLEGE variable to the proper value!
```

### New Learnings
1. The variables we set in our shell are local to it and cannot be accessed outside of it. This is to make sure that the variable data can't be viewed from other shells unless we allow it.
2. To use the variables of one shell in another shell(child shells only), we must export them using `export variable_name` command. After that, we can use them in other shells as well.
3. The *sh* command can be used to launch a child shell for program testing purpose.