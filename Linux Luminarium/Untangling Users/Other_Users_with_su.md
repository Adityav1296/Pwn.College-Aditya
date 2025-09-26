# Untangling Users

## Other Users with su
With no arguments, su will start a root shell (after authenticating with root's password). However, you can also give a username as an argument to switch to that user instead of root. For example:

```bash
hacker@dojo:~$ su some-user
Password:
some-user@dojo:~$
```

### Objective
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}`

- First I ran the `su` command with the username zardus but I intetionally gave a wrong password and the authentication failed as expected.
- Then I again ran the same command with the correct password to switch to zardus user as can be seen with the `whoami` command.
- Then I listed the files present there using `ls` and used `cat` on the flag file to get the flag.

```bash
hacker@users~other-users-with-su:~$ su zardus
Password:
su: Authentication failure
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ whoami
zardus
zardus@users~other-users-with-su:/home/hacker$ ls
Desktop  flag  home-backup.tar.gz
zardus@users~other-users-with-su:/home/hacker$ cat flag
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
```

### New Learnings
1. `su` command can be used to switch the user to another one. It is done with the `su user_name` command.