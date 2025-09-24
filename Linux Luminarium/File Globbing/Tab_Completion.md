# File Globbing

## Tab Completion
As tempting as it might be, using * to shorten what must be typed on the commandline can lead to mistakes. Your glob might expand to unintended files, and you might not spot it until the rm command is already running! No one is safe from this style of error.

A safer alternative when you are trying to specify a specific target is tab completion. If you hit tab in the shell, it'll try to figure out what you're going to type and automatically complete it. Auto-completion is super useful.

### Objective 
This challenge has copied the flag into /challenge/pwncollege, and you can freely cat that file. But you can't type the filename: we used some serious trickery to make sure that you must tab-complete it.

### Solve
**Flag:** `pwn.college{wu2Txq6YLTkSSIaZn5Ga24oTU6k.QX0QTM3EDLygjN0czW}`

-> In this challenge, after changing my directory to */challenge/*, I initially listed the files there. The pwncollege file was present there.  
-> But as the challenge objective stated, we can't access the pwncollege file by typing its name as is shown by the first insuccessful output that I got when I tried to *cat* to pwncollege directly by typing the name out.  
-> Then I again used *cat* command but this time around I only typed './pwn' and then used the Tab key to autocomplete the full name. That's how I obtained the flag.

```bash
hacker@globbing~tab-completion:~$ ls
Desktop  flag  home-backup.tar.gz
hacker@globbing~tab-completion:~$ cd /challenge
hacker@globbing~tab-completion:/challenge$ ls
DESCRIPTION.md  pwncollege​
hacker@globbing~tab-completion:/challenge$ cat ./pwncollege
bash: cd: ./pwncollege: No such file or directory
hacker@globbing~tab-completion:/challenge$ cat ./pwncollege​
pwn.college{wu2Txq6YLTkSSIaZn5Ga24oTU6k.QX0QTM3EDLygjN0czW}
```

### New Learnings
1. Looking up for files, directories or paths using only * glob pattern can easily lead to a mistake like opening up an unintended file or running some unnecessary command. To avoid that, we can use the Tab key to autocomplete what we were typing. It might not always make the correct guess while auto-completing but it is still a safer option than straightaway using * glob pattern. 