# Chaining Commands

## Scripting with Conditionals
Now that you can use arguments in scripts, let's make them smarter with conditional logic!

In bash, you can use if statements to make decisions:

```bash
if [ "$1" == "ping" ]
then
    echo "pong"
fi
```

Here, if the first argument is "ping", print out "pong". The syntax is somewhat unforgiving for a few reasons.

### Objective
For this challenge, write a script at /home/hacker/solve.sh that:
   1. Takes one argument
   2. If the argument is "pwn", output "college"
   3. For any other input, output nothing  
Once your script works correctly, run /challenge/run to get your flag!

### Solve
**Flag:** `pwn.college{klrZXx2qBtNJeBm0ozwxgwuC0rV.QX2MzM4EDLygjN0czW}`

- The first thing I did was to create the solve.sh file. Then I used `ls -l` command to list all its permission. Since it did not have any execution permission, I added the exection permission to the user.
- Then I used the `nano solve.sh` command to open the file and write the commands to be executed in it along with the shebang.
- Finally at the end, I added the argument 'pwn' to the script using the `bash` command. Since it is an 'if' statement inside the script, I got the output right away.
- Then I ran the `/challenge/run` command to verify the output and get the flag.

```bash
hacker@chaining~scripting-with-conditionals:~$ touch solve.sh
hacker@chaining~scripting-with-conditionals:~$ ls -l solve.sh
-rw-r--r-- 1 hacker hacker 0 Sep 26 19:52 solve.sh
hacker@chaining~scripting-with-conditionals:~$ chmod u+x solve.sh
hacker@chaining~scripting-with-conditionals:~$ ls -l solve.sh
-rwxr--r-- 1 hacker hacker 0 Sep 26 19:52 solve.sh
hacker@chaining~scripting-with-conditionals:~$ nano solve.sh
hacker@chaining~scripting-with-conditionals:~$ bash solve.sh pwn
college
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here is your flag:
pwn.college{klrZXx2qBtNJeBm0ozwxgwuC0rV.QX2MzM4EDLygjN0czW}
```

### New Learnings
1. We can add conditional statements like 'if' statements inside the scripts to make the scripts better.
2. However there are certain things that we need to keep in mind while adding the 'if' statements in the scripts : 
    1. You must have spaces after if, after [, and before ]. 
    2. if, then, and fi must all be on different lines (or separated by semicolons); you can't lump them into the same statement.
    3. Instead of endif or end or something like that, the terminator of the if statement is fi (if backwards).  
These are some of the basic syntax rules that we must follow.