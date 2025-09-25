# Shell Variables

## Storing Command Output
In the course of working with the shell, you will often want to store the output of some command into a variable. Luckily, the shell makes this quite easy using something called Command Substitution! Observe:

```bash
hacker@dojo:~$ FLAG=$(cat /flag)
hacker@dojo:~$ echo "$FLAG"
pwn.college{blahblahblah}
hacker@dojo:~$
```

### Objective 
Now, you practice. Read the output of the /challenge/run command directly into a variable called PWN, and it will contain the flag!

### Solve
**Flag:** `pwn.college{42MbLQhmpxLpP5CY7uteF2KTosy.dVzN0UDLygjN0czW}`

- In this challenge, I first read the output of the */challenge/run* command into the PWN variable using the method described in the challenge desciption.
- Then I used *echo* command to print that variable and got the flag.

```bash
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{42MbLQhmpxLpP5CY7uteF2KTosy.dVzN0UDLygjN0czW}
```

### New Learnings
1. We can store command outputs in files by piping them. Similarly, we can store them in variables as well in the following way : `variable_name=$(command argument)`
2. Trivia: You can also use backticks instead of $(): FLAG=`cat /flag` instead of FLAG=$(cat /flag) in the example above. This is an older format, and has some disadvantages (for example, imagine if you wanted to nest command substitutions. How would you do $(cat $(find / -name flag)) with backticks?