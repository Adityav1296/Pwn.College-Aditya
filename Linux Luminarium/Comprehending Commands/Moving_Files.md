# Comprehending Commands 

## Moving Files
You can also move files around with the mv command. The usage is simple:

```
hacker@dojo:~$ ls
my-file
hacker@dojo:~$ cat my-file
PWN!
hacker@dojo:~$ mv my-file your-file
hacker@dojo:~$ ls
your-file
hacker@dojo:~$ cat your-file
PWN!
hacker@dojo:~$
```

### Objective
This challenge wants you to move the /flag file into /tmp/hack-the-planet (do it)! When you're done, run /challenge/check, which will check things out and give the flag to you.

### Solve
**Flag:** `pwn.college{Y6YiwRVZLMH-0XEGT3ZURiExr0F.QX5ETM3EDLygjN0czW}`

-> In this challenge, I initially listed the contents of the home directory. From there, I moved the */flag* file to */tmp/hack-the-planet* as required by the challenge using the *mv* command.  
-> Then I ran the */challenge/check* command to check the task performed and obtain the flag.  

```bash
hacker@commands~moving-files:~$ ls
Desktop  flag  home-backup.tar.gz
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ cd /tmp
hacker@commands~moving-files:/tmp$ ls
bin  hack-the-planet  hsperfdata_root  tmp.TpSOPGOVKK
hacker@commands~moving-files:/tmp$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{Y6YiwRVZLMH-0XEGT3ZURiExr0F.QX5ETM3EDLygjN0czW}
```

-> Note to be taken that when I used just `mv flag /tmp/hack-the-planet` then the output was an error likely because ~/flag and /flag are 2 different copies of the same flag and are present at different locations.

```
hacker@commands~moving-files:~$ mv flag /tmp/hack-the-planet
ERROR: please make sure that you specify the flag file (/flag)
as your SOURCE! (You specified /home/hacker/flag).
```

### New Learning
1. *mv* command can be used to move files from one directory to another. The file being moved gets erased from its original location and moves to the new location specified in the argument. 