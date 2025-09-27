# Chaining Commands

## Scripting with Default Cases
Your if statements so far have handled specific cases, but what about everything else? That's where else comes in!

The else clause executes when the if condition is false:

```bash
if [ "$1" == "hello" ]
then
    echo "Hi there!"
else
    echo "I don't understand"
fi
```

Note that the else doesn't have a condition --- it catches everything that didn't match previously. It also doesn't have a then statement. Finally, the fi goes after the else block to denote the end of the whole complex statement!

```bash
if [ "$1" == "start" ]
then
    echo "Starting the service..."
else
    echo "Unknown command. Use 'start' to begin."
fi
```

### Objective
For this challenge, write a script at /home/hacker/solve.sh that:
   1. Takes one argument
   2. If the argument is "pwn", output "college"
   3. For any other input, output "nope"  
Once your script works correctly, run /challenge/run to get your flag!

### Solve
**Flag:** `pwn.college{U-cDKtJoA1j05-L__0p_kb7cT_R.QX3MzM4EDLygjN0czW}`

- The first thing I did was to create the solve.sh file. Then I used `ls -l` command to list all its permission. Since it did not have any execution permission, I added the exection permission to the user.
- Then I used the `nano solve.sh` command to open the file and write the commands to be executed in it along with the shebang.
- Finally at the end, I added the argument 'pwn' to the script using the `bash` command. Since it is an 'if-else' statement inside the script, I got the output right away.
- Then I ran the `/challenge/run` command to verify the output and get the flag.

```bash
hacker@chaining~scripting-with-default-cases:~$ touch solve.sh
hacker@chaining~scripting-with-default-cases:~$ ls -l solve.sh
-rw-r--r-- 1 hacker hacker 0 Sep 26 19:52 solve.sh
hacker@chaining~scripting-with-default-cases:~$ chmod u+x solve.sh
hacker@chaining~scripting-with-default-cases:~$ ls -l solve.sh
-rwxr--r-- 1 hacker hacker 0 Sep 26 19:52 solve.sh
hacker@chaining~scripting-with-default-cases:~$ nano solve.sh
hacker@chaining~scripting-with-default-cases:~$ bash solve.sh pwn
college
hacker@chaining~scripting-with-default-cases:~$ bash solve.sh college
nope
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here is your flag:
pwn.college{U-cDKtJoA1j05-L__0p_kb7cT_R.QX3MzM4EDLygjN0czW}
```

### New Learnings
1. In the conditional 'if' statements, we can add the 'else' statements to handle the cases that are not taken care of by 'if' statements.
2. The syntax for the block of code remanins the same. The 'else' statement is added right aftert the 'if' statements.