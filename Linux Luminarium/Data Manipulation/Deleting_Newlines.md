# Data Manipulation

## Deleting Newlines
A common class of characters to remove is a line separator. This happens when you have a stream of data that you want to turn into a single line for further processing. You can specify newlines almost like any other character, by escaping them:

```bash
hacker@dojo:~$ echo "hello_world!" | tr _ "\n"
hello
world!
hacker@dojo:~$
```

Here, the backslash (\) signifies that the character that follows it is a standin for a character that's hard to input into the shell normally. The newline, of course, is hard to input because when you typically hit Enter, you'll run the command itself. \n is a standin for this newline, and it must be in quotes to prevent the shell interpreter itself from trying to interpret it and pass it to tr instead.

### Objective
In this challenge, we'll inject a bunch of newlines into the flag. Delete them with tr's -d flag and the escaped newline specification!

### Solve
**Flag:** `pwn.college{A1UySWGZS4pWCtdTtiv2QVxFWpi.QX1ETM3EDLygjN0czW}`

- In this challenge, I straightaway used the piping operator to pipe the output of */challenge/run* command and on the other side, I used *tr -d* command as specified. This time since we need to delete the newline character, it is necessary that we specify it in ' ' like '\n' to make sure that the shell interpreter itself from trying to interpret it.

```bash
hacker@data~deleting-newlines:~$ /challenge/run | tr -d '\n'
Your line-split flag: pwn.college{A1UySWGZS4pWCtdTtiv2QVxFWpi.QX1ETM3EDLygjN0czW}
```

### New Learnings
1. The '\' character is called the escape character.
2. When using special characters with the *tr* command, it is necessary to specify them in `'character'` to prevent any unintended action by the shell to take place.

### References 
1. [GeeksforGeeks : tr command in Unix/Linux with examples](https://www.geeksforgeeks.org/linux-unix/tr-command-in-unix-linux-with-examples/)
