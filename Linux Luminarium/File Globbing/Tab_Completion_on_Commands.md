# File Globbing

## Tab Completion
Tab completion is for more than files! You can also tab-complete commands.

You can auto-complete any command, but be careful: callous auto-completes without double-checking the result can wreak havoc in your shell if you accidentally run the wrong commands!

### Objective 
This level has a command that starts with pwncollege, and it'll give you the flag. Type pwncollege and hit the tab key to auto-complete it

### Solve
**Flag:** `pwn.college{EJ0Mbofq2ZQST9V8NLslVOzQFFX.QX1QTM3EDLygjN0czW}`

-> In this challenge, I straightaway started by typing pwn and then using tab to auto-complete. I first wanted to check if there were other files that started with pwn. On the first try, since tab did not auto-complete the command, I pressed tab again to get the multiple options available.  
-> The pwncollege command was one of the options listed. So I just typed out the name of the command to get the flag.  
-> I also tried it by using tab to auto-complete. I typed 'pwncollege' before using tab this time. This was, the word I typed was already unique among the options available and tab auto-completed it on its own. 

```bash
hacker@globbing~tab-completion-on-commands:~$ pwn
pwn               pwndbg            pwntools-gdb
pwncollege-27940  pwnstrip
hacker@globbing~tab-completion-on-commands:~$ pwncollege-27940
Correct! Here is your flag:
pwn.college{EJ0Mbofq2ZQST9V8NLslVOzQFFX.QX1QTM3EDLygjN0czW}
hacker@globbing~tab-completion-on-commands:~$ pwncollege-27940
Correct! Here is your flag:
pwn.college{EJ0Mbofq2ZQST9V8NLslVOzQFFX.QX1QTM3EDLygjN0czW}
```

### New Learnings
1. Tab completion works not only when passing file or directory names to a command but also on commands themselves. However, it is important to check the command once it has been auto-completed to make sure that it is the correct command that we want to run and not some other command.