Did you think you, hacker, are alone in the workspace? There are MANY users on a typical Linux system! The full list of users on a Linux system is specified in the /etc/passwd file (named so for historical reasons --- it doesn't actually hold passwords anymore). Here is an example from the dojo container:

```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mysql:x:104:105:MySQL Server,,,:/nonexistent:/bin/false
messagebus:x:105:106::/nonexistent:/usr/sbin/nologin
sshd:x:106:65534::/run/sshd:/usr/sbin/nologin
hacker:x:1000:1000::/home/hacker:/bin/bash
```

A lot of users here, and a lot of info! Each line contains, separated by :s, the username, an x as a placeholder for where the password used to be (we'll cover where it actually is later), the numerical user ID, the numerical default group ID, long-form user details, the home directory, and the default shell.

One important user is root: the system administrator. The system administrator has obvious security implications: a hacker user that can somehow, through various functionalities of Linux, become the root user would be able to wreak havoc on the system. A very frequent goal of hackers breaking into systems is to escalate to root, and thus root must be defended at all cost!