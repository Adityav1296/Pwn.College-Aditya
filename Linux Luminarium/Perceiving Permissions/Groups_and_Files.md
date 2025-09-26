# Perceiving Permissions

## Groups and Files
Files have both an owning user and group. A group can have multiple users in it, and a user can be a member of multiple groups. You can check what groups you are part of with the id command:

```bash
hacker@dojo:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@dojo:~$
```

A typical main user of a typical Linux desktop has a lot of groups. For example, this is Zardus' desktop:

```bash
zardus@yourcomputer:~$ id
uid=1000(zardus) gid=1000(zardus) groups=1000(zardus),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),100(users),106(netdev),114(bluetooth),117(lpadmin),120(scanner),995(docker)
zardus@yourcomputer:~$
```

Any member of a group can interact with all the files and directories that the group owns keeping in mind the permissions given to the group by the file or directory.

Group ownership can be changed with the chgrp (change group) command! Unless you have write access to the file and membership in the new group, this typically requires root access, so let's check it out as root:

```bash
root@dojo:~# mkdir pwn_directory
root@dojo:~# touch college_file
root@dojo:~# ls -l
total 4
-rw-r--r-- 1 root root    0 May 22 13:42 college_file
drwxr-xr-x 2 root root 4096 May 22 13:42 pwn_directory
root@dojo:~# chgrp hacker college_file
root@dojo:~# ls -l
total 4
-rw-r--r-- 1 root hacker    0 May 22 13:42 college_file
drwxr-xr-x 2 root root   4096 May 22 13:42 pwn_directory
root@dojo:~#
```

### Objective 
In this level, I have made the flag readable by whatever group owns it, but this group is currently root. Luckily, I have also made it possible for you to invoke chgrp as the hacker user! Change the group ownership of the flag file, and read the flag!

### Solve
**Flag:** `pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}`

- First I used the `id` command to check the group I am a part of. Then using `ls -l` command, I listed all the files with the info about the groups that own them.
- Then I used the `chgrp` command to change the group of flag file from root to hacker and again listed the files to confirm the changes.
- Then I just used `cat` command to get the flag.

```bash
hacker@permissions~groups-and-files:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@permissions~groups-and-files:~$ ls -l
total 144
drwxr-xr-x 1 hacker hacker      0 Sep 22 04:01 Desktop
-rw-r--r-- 1 hacker root       58 Sep 23 03:45 flag
-rw-r--r-- 1 hacker hacker 142758 Sep 21 15:40 home-backup.tar.gz
hacker@permissions~groups-and-files:~$ chgrp hacker flag
hacker@permissions~groups-and-files:~$ ls -l
total 144
drwxr-xr-x 1 hacker hacker      0 Sep 22 04:01 Desktop
-rw-r--r-- 1 hacker hacker     58 Sep 23 03:45 flag
-rw-r--r-- 1 hacker hacker 142758 Sep 21 15:40 home-backup.tar.gz
hacker@permissions~groups-and-files:~$ cat flag
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
```

### New Learnings
1. The group ownership of the files can be changed using the `chgrp` command in the following way :

```bash
chgrp [groupname] [file]
```

2. We can use the `id` command to check which groups we are a part of.
3. Any user who is a part of a group can access the files that the group owns and perform tasks on them keeping in mind the permissions provided to the group with respect to that particular file.
4. A user can be a part of multiple groups and a group can own multiple files.