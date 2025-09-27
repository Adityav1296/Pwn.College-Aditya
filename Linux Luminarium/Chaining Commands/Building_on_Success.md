# Chaining Commands

## Building on Success
The && operator allows you to run a second command only if the first command succeeds (in Linux convention, this means it exited with code 0). This is called the "AND" operator because both conditions must be true: the first command must succeed AND then the second command will run. That's super useful for complex commandline workflows where certain actions depend on the success of other actions.

Here's the syntax:

```bash
hacker@dojo:~$ command1 && command2
```

This means: "Run command1, and IF it succeeds, then run command2." Example :

```bash
hacker@dojo:~$ touch /home/hacker/file && echo "this will run"
success
this will run
hacker@dojo:~$ touch /file && echo "this will NOT run"
touch: cannot touch '/file': Permission denied
hacker@dojo:~$
```

### Objective
In this challenge, you need to chain the programs /challenge/first-success and /challenge/second using the && operator.

### Solve
**Flag:** `pwn.college{4pnaz1IwW1nETVJ3ON5NDE_ba5S.QXyQzM4EDLygjN0czW}`

- In this challenge, I first ran the two given commands separately to see if something happens. As a result the error was generated.
- So I chained the two commands using `&&` and then ran them to get the flag.

```bash
hacker@chaining~building-on-success:~$ /challenge/first-success
hacker@chaining~building-on-success:~$ /challenge/second
Error: /challenge/first-success must be successfully chained with
/challenge/second using &&
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{4pnaz1IwW1nETVJ3ON5NDE_ba5S.QXyQzM4EDLygjN0czW}
```

### New Learnings
1. Two commands can be chained together using `&&`. The working for it is that the first command should execute successfully i.e it should exit with exit code 0. Only then will the second command execute else it will not.
2. It is useful in scenarios where the second command depends on the success of the first one. 