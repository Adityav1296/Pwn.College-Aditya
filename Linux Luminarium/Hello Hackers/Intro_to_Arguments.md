# Hello Hackers

## Intro to Arguments
Arguments are the additional data passed to the commands.\
When you type a line of text and hit enter, the shell actually parses your input into a command and its arguments. The first word is the command, and the subsequent words are arguments.

```
hacker@dojo:~$ echo Hello
Hello
hacker@dojo:~$
```

Let's look at echo with multiple arguments:

```
hacker@dojo:~$ echo Hello Hackers!
Hello Hackers!
hacker@dojo:~$
```

### Objective
In this challenge, to get the flag, you must run the hello command with a single argument of hackers.

### Solve
**Flag:** `pwn.college{k37zHiiBvglTBqXGuuZ8b65uGgC.dhjNyUDLygjN0czW}`

-> In this challenge, I executed the hello command as required with the argument as hackers to get the flag. 
-> I also executed the 'echo' command given in the challenge description.

```bash
hacker@hello~intro-to-arguments:~$ echo lets solve all these challenges
lets solve all these challenges
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{k37zHiiBvglTBqXGuuZ8b65uGgC.dhjNyUDLygjN0czW}
```

### New Learning
1. Learnt how arguments work with commands
2. Learnt how echo command can be used to either print the text we want onto the terminal.
3. Tried the echo command with some special characters. In most of the cases, it just prints the text onto the terminal.
   - When '&' and '*' were used, along with printing the text onto the terminal it also displayed extra text like : [1] 145 for '&' and [1]+  Done for '*'.
   - Displayed -> bash: syntax error near unexpected token `(' \ when parenthesis were used.
   - On using " ' ", it didn't print anything and stalled instead.

```
hacker@hello~intro-to-arguments:~$ echo lets solve all these challenges!
lets solve all these challenges!
hacker@hello~intro-to-arguments:~$ echo lets solve all these challenges!#
echo lets solve all these challengesecho lets solve all these challenges
lets solve all these challengesecho lets solve all these challenges
hacker@hello~intro-to-arguments:~$ echo lets solve all these challenges@
lets solve all these challenges@
hacker@hello~intro-to-arguments:~$ echo lets solve all these challenges#
lets solve all these challenges#
hacker@hello~intro-to-arguments:~$ echo lets solve all these challenges$
lets solve all these challenges$
hacker@hello~intro-to-arguments:~$ echo lets solve all these challenges%
lets solve all these challenges%
hacker@hello~intro-to-arguments:~$ echo lets solve all these challenges^
lets solve all these challenges^
hacker@hello~intro-to-arguments:~$ echo lets solve all these challenges&
[1] 145
lets solve all these challenges
hacker@hello~intro-to-arguments:~$ echo lets solve all these challenges*
lets solve all these challenges*
[1]+  Done                    echo lets solve all these challenges
hacker@hello~intro-to-arguments:~$ echo lets solve all these challenges(
bash: syntax error near unexpected token `('
hacker@hello~intro-to-arguments:~$ echo lets solve all these challenges()
bash: syntax error near unexpected token `('
hacker@hello~intro-to-arguments:~$ echo let's
>
```
