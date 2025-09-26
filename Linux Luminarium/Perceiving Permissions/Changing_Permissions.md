# Perceiving Permissions

## Changing Permissions
Each character of the three represent permission for a different type:

```bash
r - user/group/other can read the file (or list the directory)
w - user/group/other can modify the files (or create/delete files in the directory)
x - user/group/other can execute the file as a program (or can enter the directory, e.g., using `cd`)
- - nothing 
```

Like ownership, file permissions can also be changed. This is done with the chmod (change mode) command. The basic usage for chmod is:

```bash
chmod [OPTIONS] MODE FILE
```

You can specify the MODE in two ways: as a modification of the existing permissions mode, or as a completely new mode to overwrite the old one. Modifying an existing mode: chmod allows you to tweak permissions with the mode format of WHO+/-WHAT, where WHO is user/group/other and WHAT is read/write/execute. For example, to add read access for the owning user, you would specify a mode of u+r. So:

```bash
root@dojo:~# mkdir pwn_directory
root@dojo:~# touch college_file
root@dojo:~# ls -l
total 4
-rw-r--r-- 1 root root    0 May 22 13:42 college_file
drwxr-xr-x 2 root root 4096 May 22 13:42 pwn_directory
root@dojo:~# chmod go-rwx *
root@dojo:~# ls -l
total 4
-rw------- 1 hacker root    0 May 22 13:42 college_file
drwx------ 2 root   root 4096 May 22 13:42 pwn_directory
root@dojo:~#
```

### Objective 
In this challenge, you must change the permissions of the /flag file to read it! The /flag file is owned by root, and you can't change that, but you can make it readable. Go and solve this!

### Solve
**Flag:** `pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}`

- In this challenge, initially I listed all the files with the permissions they have been assigned using the `ls -l` command.
- The flag file already allowed read access to the user, group and others. That means we can just read the flag file and get the flag. Since the owner and the group that owns the file are both root, that means we are in the others.
- So I then removed the read permission from the others and showed the effect using the `cat flag` command. Then I again added the read permission to the others and used `cat` to read the flag.

```bash
hacker@permissions~changing-permissions:~$ ls -l
total 144
drwxr-xr-x 1 hacker hacker      0 Sep 22 04:01 Desktop
-rw-r--r-- 1 root   root       58 Sep 23 03:45 flag
-rw-r--r-- 1 hacker hacker 142758 Sep 21 15:40 home-backup.tar.gz
hacker@permissions~changing-permissions:~$ chmod u-r flag
hacker@permissions~changing-permissions:~$ ls -l
total 144
drwxr-xr-x 1 hacker hacker      0 Sep 22 04:01 Desktop
-rw-r----- 1 root   root       58 Sep 23 03:45 flag
-rw-r--r-- 1 hacker hacker 142758 Sep 21 15:40 home-backup.tar.gz
hacker@permissions~changing-permissions:~$ cat flag
cat: flag: Permission denied
hacker@permissions~changing-permissions:~$ chmod o+r flag
hacker@permissions~changing-permissions:~$ cat flag
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
```

### New Learnings
1. We use the `chmod` command to change the permissions of the different entities in a file. 
2. The different permissions are :
   1. r - read file
   2. w - write to file
   3. x - execute the file
3. The different entities are :
   1. u - user
   2. g - group
   3. o - others
4. We don't have to be the root user to use the `chmod` command. Both the root user and the owner of the file can set permissions for the file.
5. The permissions for files can also be set using specific numbers :
   1. r = 4
   2. w = 2
   3. x = 1

```bash
hacker@permissions~permission-tweaking-practice:~$ ls -l /flag
-r-------- 1 hacker hacker 58 Sep 26 12:39 /flag
hacker@permissions~permission-tweaking-practice:~$ chmod 641 /flag
hacker@permissions~permission-tweaking-practice:~$ ls -l /flag
-rw-r----x 1 hacker hacker 58 Sep 26 12:39 /flag
```