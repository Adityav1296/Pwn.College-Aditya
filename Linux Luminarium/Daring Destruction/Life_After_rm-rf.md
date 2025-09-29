# Daring Destruction

## Life After rm -rf /
Let's dig into the effects of blowing away your whole filesystem. You're now an experienced rmer, but previously, /challenge/check printed the flag out for you when you cleared away the clutter of the filesystem. What if it hadn't? Without cat, how would you read that /flag?

Recall, from the Digesting Documentation module, that some shell commands are builtins. While ls, cat, and such aren't, read is. That means that, even if you blow away your whole filesystem, as long as you have an already-running instance of bash, you can read files!

### Objective
This challenge will force you to try it. It's almost the same as the previous one, but you must read the flag yourself after you destroy the system. After you rm everything, your previously-launched /challenge/check will restore the /flag file and make it readable. Then you can read it!

### Solve
**Flag:** `pwn.college{Quizmufb_bLAonpoxRBdQbLQMIN.QXzMTM3EDLygjN0czW}`

- In this challenge, I simply ran the /challenge/check command in the background and once it started, I used `rm --no-preserve-root -rf /` command to wipe out the entire disk. At the end, I used the `read` command to read the flag into a variable and the echoed that variable to the terminal.
- The thing is I somehow ended up with two flags with only one of them being correct.

```bash
hacker@destruction~life-after-rm-rf-:~$ /challenge/check &
[1] 150
hacker@destruction~life-after-rm-rf-:~$ Looks like you haven't wiped the system! We'll check again in 5 seconds...
rm --no-preLooks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
^VLooks like you haven't wiped the system! We'll check again ihacker@destruction~life-after-rm-rf-:~$           rm --no-preserve-root -rf /e-root -rf /
/bin/rm: unrecognized option '--no-rm'
Try '/bin/rm --help' for more information.
hacker@destruction~life-after-rm-rf-:~$ Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in hacker@destruction~life-after-rm-rf-:~$ rm --no-preserve-root -rf /no-preserve-root -rf /
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
/bin/rm: skipping '/sys', since it's on a different device
/bin/rm: skipping '/home/hacker', since it's on a different device
Looks like you haven't wiped the system! We'll check again in 5 seconds...
/bin/rm: skipping '/run/dojo/sys', since it's on a different device
/bin/rm: skipping '/proc', since it's on a different device
/bin/rm: skipping '/dev', since it's on a different device
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
/bin/rm: skipping '/nix', since it's on a different device
hacker@destruction~life-after-rm-rf-:~$ YES! You did it again! Go read the flag!
read /flag
bash: read: `/flag': not a valid identifier
[1]+  Done                    /challenge/check
hacker@destruction~life-after-rm-rf-:~$ read flag
^C
hacker@destruction~life-after-rm-rf-:~$ ls
bash: ls: command not found
hacker@destruction~life-after-rm-rf-:~$ read /flag > x.txt
bash: read: `/flag': not a valid identifier
hacker@destruction~life-after-rm-rf-:~$ read flag > x.txt
^C
hacker@destruction~life-after-rm-rf-:~$ read << flag
> ^C
hacker@destruction~life-after-rm-rf-:~$ read < flag
hacker@destruction~life-after-rm-rf-:~$ flag 
bash: flag: command not found
hacker@destruction~life-after-rm-rf-:~$ ./falg
bash: ./falg: No such file or directory
hacker@destruction~life-after-rm-rf-:~$ ./flag
bash: ./flag: Permission denied
hacker@destruction~life-after-rm-rf-:~$ echo flag
flag
hacker@destruction~life-after-rm-rf-:~$ read x.txt < flag
bash: read: `x.txt': not a valid identifier
hacker@destruction~life-after-rm-rf-:~$ read x < flag
hacker@destruction~life-after-rm-rf-:~$ echo "$x"
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
hacker@destruction~life-after-rm-rf-:~$ read y < /flag
hacker@destruction~life-after-rm-rf-:~$ echo "$y"
pwn.college{Quizmufb_bLAonpoxRBdQbLQMIN.QXzMTM3EDLygjN0czW}
```

### New Learnings
1. Even if the filesystem has been wiped out, we can still use the inbuilt shell commands such as `read`. This way we can still work with the terminal to an extent.