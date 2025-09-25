# Shell Variables

## Printing Variables
Let's start with printing variables out. The /challenge/run program will not, and cannot, give you the flag, but that's okay, because the flag has been put into the variable called "FLAG"! Just have your shell print it out!

You can accomplish this using a number of ways, but we'll start with echo. This command just prints stuff. For example:

```bash
hacker@dojo:~$ echo Hello Hackers!
Hello Hackers!
```

You can also print out variables with echo, by prepending the variable name with a $.

### Objective 
Have your shell print out the FLAG variable and solve this challenge!

### Solve
**Flag:** `pwn.college{AEKr6od7R9mt10CRR_IEGw5miq4.ddTN1QDLygjN0czW}`

- This was a direct challenge where I used the *echo* command with the given FLAG variables and obtained the flag.

```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{AEKr6od7R9mt10CRR_IEGw5miq4.ddTN1QDLygjN0czW}
```

### New Learnings
1. *echo* can be used to print variables as well provided that we append the variable name to '$' before printing it. Example :

```bash
hacker@dojo:~$ echo $PWD
/home/hacker
```