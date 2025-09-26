# Perceiving Permissions

## Changing File Ownership
First things first: file ownership. Every file in Linux is owned by a user on the system. Most often, in your day-to-day life, that user is the user you log in as every day. The two most important user accounts are:

  1. Your user account!
  2. root. This is the administrative account and, in most security situations, the ultimate prize.

```bash
hacker@dojo:~$ ls -l /flag
-r-------- 1 root root 53 Jul  4 04:47 /flag
hacker@dojo:~$ cat /flag
cat: /flag: Permission denied
hacker@dojo:~$
```

Here, you can see that the flag is owned by the root user (the first root in that line) and the root group (the second root in that line). When we try to read it as the hacker user, we are denied. However, if we were root (a hacker's dream!), we would have no problem reading this file:

```bash
root@dojo:~# cat /flag
pwn.college{demo_flag}
root@dojo:~#
```

We can change the ownership of files! This is done via the chown (change owner) command. Typically, chown can only be invoked by the root user.

```bash
root@dojo:~# mkdir pwn_directory
root@dojo:~# touch college_file
root@dojo:~# ls -l
total 4
-rw-r--r-- 1 root root    0 May 22 13:42 college_file
drwxr-xr-x 2 root root 4096 May 22 13:42 pwn_directory
root@dojo:~# chown hacker college_file
root@dojo:~# ls -l
total 4
-rw-r--r-- 1 hacker root    0 May 22 13:42 college_file
drwxr-xr-x 2 root   root 4096 May 22 13:42 pwn_directory
root@dojo:~#
```

### Objective 
In this level, we will practice changing the owner of the /flag file to the hacker user, and then read the flag. For this challenge only, I made it so that you can use chown to your heart's content as the hacker user.

### Solve
**Flag:** `pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}`

- First I listed all the files with the information about the owners of the file using the `ls -l` command. 
- Then I used `chown` command to change the user who owns the flag file from root to hacker and again listed the files using `ls -l` to confirm the changes.
- Then I simply used the `cat` command to get the flag.

```bash
hacker@permissions~changing-file-ownership:~$ ls -l
total 144
drwxr-xr-x 1 hacker hacker      0 Sep 22 04:01 Desktop
-rw-r--r-- 1 root   root       58 Sep 23 03:45 flag
-rw-r--r-- 1 hacker hacker 142758 Sep 21 15:40 home-backup.tar.gz
hacker@permissions~changing-file-ownership:~$ chown hacker flag
hacker@permissions~changing-file-ownership:~$ ls -l
total 144
drwxr-xr-x 1 hacker hacker      0 Sep 22 04:01 Desktop
-rw-r--r-- 1 hacker root       58 Sep 23 03:45 flag
-rw-r--r-- 1 hacker hacker 142758 Sep 21 15:40 home-backup.tar.gz
hacker@permissions~changing-file-ownership:~$ cat flag
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
```

### New Learnings
1. The ownership of the files can be changed using the `chown` command in the following way :

```bash
chown [username] [file]
```

2. The `chown` command is generally reserved only for the root user else it might be misused and cause a security risk.

3. `ls -l` command lists the files present in the directory along with additional info about them like the permissions given to different entities regarding the file, owner of the file, group that owns the files.