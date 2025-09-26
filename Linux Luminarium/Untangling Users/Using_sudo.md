# Untangling Users

## Using sudo
Unlike su, which defaults to launching a shell as a specified user, sudo defaults to running a command as root:

```bash
hacker@dojo:~$ whoami
hacker
hacker@dojo:~$ sudo whoami
root
hacker@dojo:~$
```

Unlike su, which relies on password authentication, sudo checks policies to determine whether the user is authorized to run commands as root. These policies are defined in /etc/sudoers.

### Objective
In this level, we will give you sudo access, and you will use it to read the flag.

### Solve
**Flag:** `pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}`

- Since sudo access was already given from the start, I just listed the files in the directory using `ls` command and the used `cat` command to get the flag from the flag file.

```bash
hacker@users~using-sudo:~$ ls
Desktop  flag  home-backup.tar.gz
hacker@users~using-sudo:~$ cat flag
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
```

### New Learnings
1. **sudo** works just like the **su** command by giving root privivleges. The difference is that, su requires a root password to login as the root user. There are security risks associated with the root password like leaks. Instead, sudo defaults to running commands as root  and checks policies to determine whether the user is authorized to run commands as root.
