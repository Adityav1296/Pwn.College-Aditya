# Chaining Commands

## Scripting with Multiple Conditions
If you need to check multiple conditions? You can use elif (short for else if):

```bash
if [ "$1" == "one" ]
then
    echo "1"
elif [ "$1" == "two" ]
then
    echo "2"
elif [ "$1" == "three" ]
then
    echo "3"
else
    echo "unknown"
fi
```

Note that you do need a then after the elif, just like the if. As before the else at the end catches everything that didn't match.

### Objective
For this challenge, write a script at /home/hacker/solve.sh that:
   1. Takes one argument
   2. If the argument is "hack", output "the planet"
   3. If the argument is "pwn", output "college"
   4. If the argument is "learn", output "linux"
   5. For any other input, output "unknown"  
Once your script works correctly, run /challenge/run to get your flag!

### Solve
**Flag:** `pwn.college{g_2_-iQ7Y4FoB128nEtVo8dZPhs.QX4MzM4EDLygjN0czW}`

- The first thing I did was to create the solve.sh file. Then I used `ls -l` command to list all its permission. Since it did not have any execution permission, I added the exection permission to the user.
- Then I used the `nano solve.sh` command to open the file and write the commands to be executed in it along with the shebang.
- Finally at the end, I added the arguments 'pwn', 'learn' and 'hack' to the script using the `bash` command. Since it is an 'if-elif-else' statement inside the script, I get the output right away.
- Then I ran the `/challenge/run` command to verify the output and get the flag.

```bash
hacker@chaining~scripting-with-multiple-conditions:~$ touch solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ ls -l solve.sh
-rw-r--r-- 1 hacker hacker 0 Sep 26 19:52 solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ chmod u+x solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ ls -l solve.sh
-rwxr--r-- 1 hacker hacker 0 Sep 26 19:52 solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ nano solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ bash solve.sh pwn
college
hacker@chaining~scripting-with-multiple-conditions:~$ bash solve.sh pwn
college
hacker@chaining~scripting-with-multiple-conditions:~$ bash solve.sh learn
linux
hacker@chaining~scripting-with-multiple-conditions:~$ bash solve.sh hack
the planet
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here is your flag:
pwn.college{g_2_-iQ7Y4FoB128nEtVo8dZPhs.QX4MzM4EDLygjN0czW}
```

### New Learnings
1. In the conditional 'if' statements, we can add the 'elif' statements and use them to handle multiple conditions. The 'else' statement stays at the end of the 'if-elif' statments.
2. We need to follow the same rules while writing the 'elif' statements as we did with the 'if' statements.