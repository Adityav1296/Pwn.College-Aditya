# Daring Destruction

## rm -rf /
Want to wipe the slate clean and start over? You can!

```bash
hacker@dojo:~$ ls /
bin etc blah blah blah
hacker@dojo:~$ rm -rf /
hacker@dojo:~$ ls /
bash: ls: command not found
hacker@dojo:~$
```

What happened here? As you recall, rm removes files. The -r (recursive) flag removes directories and all files containing them. The -f (force) flag ignores any errors the rm command runs into or compulsions that it may have. Combined and aimed at /, the results are catastrophic: a full wipe of your system. 

### Objective
In this challenge, you will do something that you might never do again: wipe the whole system. We've actually modified things a bit to keep your home directory safe (normally, it would get wiped as well!). But before you wipe it all, make sure to start /challenge/check so that it can watch the fireworks (and give you the flag)!

### Solve
**Flag:** `pwn.college{4Aq0IpYdY5bLSb0ui1l_uQoE7xa.QXyMTM3EDLygjN0czW}`

- In this challenge, I simply ran the /challenge/check command in the background and once it started, I used `rm --no-preserve-root -rf /` command to wipe out the entire disk. At the end, the check program gave me the flag.

```bash
hacker@destruction~rm-rf-:~$ /challenge/check &
[1] 150
hacker@destruction~rm-rf-:~$ Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
rm --no-preserve-root -rf /
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
/bin/rm: cannot remove '/etc/hosts': Device or resource busy
/bin/rm: cannot remove '/etc/resolv.conf': Device or resource busy
/bin/rm: cannot remove '/etc/hostname': Device or resource busy
Looks like you haven't wiped the system! We'll check again in 5 seconds...
/bin/rm: cannot remove '/usr/sbin/docker-init': Device or resource busy
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
/bin/rm: skipping '/sys', since it's on a different device
/bin/rm: skipping '/home/hacker', since it's on a different device
/bin/rm: skipping '/run/dojo/sys', since it's on a different device
/bin/rm: skipping '/proc', since it's on a different device
/bin/rm: skipping '/dev', since it's on a different device
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
/bin/rm: skipping '/nix', since it's on a different device
hacker@destruction~rm-rf-:~$ YES! You wiped it, you wild hacker! The flag is yours:
pwn.college{4Aq0IpYdY5bLSb0ui1l_uQoE7xa.QXyMTM3EDLygjN0czW}
```

### New Learnings
1. We can even delete the entire disk and filesystem using the `rm` command with correct options.
