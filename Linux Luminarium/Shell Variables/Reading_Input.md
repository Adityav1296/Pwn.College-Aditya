# Shell Variables

## Reading Input
Reading input from the user is using the aptly named read builtin, which reads input into a variable! Here is an example using the -p argument, which lets you specify a prompt: 

```bash
hacker@dojo:~$ read -p "INPUT: " MY_VARIABLE
INPUT: Hello!
hacker@dojo:~$ echo "You entered: $MY_VARIABLE"
You entered: Hello!
```

Keep in mind, read reads data from your standard input! The first Hello!, above, was inputted rather than outputted. 

### Objective 
In this challenge, your job is to use read to set the PWN variable to the value COLLEGE. Good luck!

### Solve
**Flag:** `pwn.college{8M90dKY50brd1ObrAZaBe1L_CHT.dhzN1QDLygjN0czW}`

- In this challenge, I read the user input by using the *read* command and also specified the INPUT prompt using -p argument. From there I obtained the flag.

```
hacker@variables~reading-input:~$ read -p "INPUT:" PWN
INPUT:COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{8M90dKY50brd1ObrAZaBe1L_CHT.dhzN1QDLygjN0czW}
hacker@variables~reading-input:~$ echo OUTPUT: $PWN
OUTPUT: COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{8M90dKY50brd1ObrAZaBe1L_CHT.dhzN1QDLygjN0czW}
```

### New Learnings
1. We can take user input for the values in the variables. That is done by using the *read* command. 
2. We can also specify the prompt for the *read* command using '-p' argument.
