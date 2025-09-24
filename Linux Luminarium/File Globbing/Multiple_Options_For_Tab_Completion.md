# File Globbing

## Multiple Options for Tab Completion
Consider the following situation:

```bash
hacker@dojo:~$ ls
flag  flamingo  flowers
hacker@dojo:~$ cat f<TAB>
```

There are multiple options! What happens?

What happens varies based on the specific shell and its options. By default bash will auto-expand until the first point when there are multiple options (in this case, fl). When you hit tab a second time, it'll print out those options. Other shells and configurations, instead, will cycle through the options.

### Objective 
This challenge has a /challenge/files directory with a bunch of files starting with pwncollege. Tab-complete from /challenge/files/p or so, and make your way to the flag!

### Solve
**Flag:** `pwn.college{EPTxkFXpZTckKkzFxtEL8uMR88o.QX2QTM3EDLygjN0czW}`

-> In this challenge, after changing my directory to */challenge/files*, I initially tried to list the files in there just to check but was denied.  
-> Then first I typed `cat pw` and used Tab to autocomplete. It autocompleted to 'pwn'. Then I again used the Tab to list out all the multiple options available.  
-> From there, I found the pwncollege-flag and used *cat* command with it to get the flag.

```bash
hacker@globbing~multiple-options-for-tab-completion:~$ cd /challenge/files
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ ls
No ls for you in this level! Use tab-completion instead!
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn
pwn                    pwncollege-family      pwncollege-flyswatter
pwn-college            pwncollege-flag        pwncollege-hacking
pwn-the-planet         pwncollege-flamingo
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-flag
pwn.college{EPTxkFXpZTckKkzFxtEL8uMR88o.QX2QTM3EDLygjN0czW}
```

### New Learnings
1. Tab can be used to auto-complete the word but it can also be used to list the multiple auto-complete options available in case they have common letters in them at the same position. In such case, we can manually choose the desired word to complete the command.