# Untangling Users

## Becoming Root with su
It's not just hackers that need to become root. Oftentimes, you, as the owner of your computer, need to use root access to administer it. Becoming root is a fairly common action that Linux users take, and there are two utilities that exist for this purpose: su and sudo.

su is a setuid binary:

```bash
hacker@dojo:~$ ls -l /usr/bin/su
-rwsr-xr-x 1 root root 232416 Dec 1 11:45 /usr/bin/su
hacker@dojo:~$
```

Because it has the SUID bit set, su runs as root. Running as root, it can start a root shell! Of course, su is discerning: before allowing the user to elevate privileges to root, it checks to make sure that the user knows the root password:

```bash
hacker@dojo:~$ su
Password: 
su: Authentication failure
hacker@dojo:~$
```

Modern systems very rarely have root passwords, and different mechanisms are used to grant administrative access.

### Objective
But THIS challenge (and only this challenge) does have a root password. That password is hack-the-planet, and you must provide it to su to become root! Go do that, and read the flag!

### Solve
**Flag:** `pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}`

- First I just ran the `su` command and gave the password to the terminal that is provided to us in the challenge objective. 
- Then I used `ls` command to list out the files present in the directory. After confirming the flag file, I just ran the `cat` command and got the flag.

```bash
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# ls
Desktop  H  data  flag  home-backup.tar.gz  pwn_output
root@users~becoming-root-with-su:/home/hacker# cat flag
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
```

### New Learnings
1. `su` command can be used to start a root shell given that we provide the root password to the terminal.
2. Also whenever an executable file has the SUID bit set (s), it generally runs with the privileges of the root user instead of the normal user as is shown in the challenge description above.