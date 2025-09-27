# Chaining Commands

## Handling Failure
The || operator allows you to run a second command only if the first command fails (exits with a non-zero code). This is called the "OR" operator because either the first command succeeds OR the second command will run.

Here's the syntax:

```bash
hacker@dojo:~$ command1 || command2
```

This means: "Run command1, and IF it fails, then run command2." Example :

```bash
hacker@dojo:~$ touch /file || echo "touch failed, so this runs"
touch: cannot touch '/file': Permission denied
touch failed, so this runs
hacker@dojo:~$ touch /home/hacker/file || echo "this will NOT run"
hacker@dojo:~$
```

### Objective
In this challenge, you need to chain /challenge/first-failure and /challenge/second using the || operator.

### Solve
**Flag:** `pwn.college{EKvfMt6kmgSIwTUXr_mUACGd5EM.QXzQzM4EDLygjN0czW}`

- In this challenge, I first ran the two given commands separately to see if something happens. As a result the error was generated.
- So I chained the two commands using `||` and then ran them to get the flag.

```bash
hacker@chaining~handling-failure:~$ /challenge/first-failure
hacker@chaining~handling-failure:~$ /challenge/second
Error: /challenge/first-failure must be successfully chained with
/challenge/second using ||
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{EKvfMt6kmgSIwTUXr_mUACGd5EM.QXzQzM4EDLygjN0czW}
```

### New Learnings
1. Two commands can be chained together using `||`. The working for it is that should the first command fail i.e it should exit with exit code 1, then the second command will execute else it will not.
2. It is useful in scenarios where the second command is needed as a contingency plan in case the first command fails.