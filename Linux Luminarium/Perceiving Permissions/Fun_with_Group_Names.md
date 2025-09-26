# Perceiving Permissions

## Fun with Group Names
You may have noticed that your hacker user is a member of the hacker group. There is a convention in Linux that every user has their own group, but this does not have to be the case. For example, many computer labs will put all of their users into a single, shared users group.

### Objective 
I'll still allow you to use chgrp, but I have randomized the name of the group that your user is in. You will need to use the id command to figure that name out, then chgrp to victory!

### Solve
**Flag:** `pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}`

- First I used the `id` command to check the group I am a part of. Then using `ls -l` command, I listed all the files with the info about the groups that own them.
- Then I used the `chgrp` command to change the group of flag file from root to the new group that I am a part of and again listed the files to confirm the changes.
- Then I just used `cat` command to get the flag.

```bash
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp255) groups=1000(grp255)
hacker@permissions~fun-with-groups-names:~$ ls -l
total 144
drwxr-xr-x 1 hacker grp255      0 Sep 22 04:01 Desktop
-rw-r--r-- 1 root   root       58 Sep 23 03:45 flag
-rw-r--r-- 1 hacker grp255 142758 Sep 21 15:40 home-backup.tar.gz
hacker@permissions~fun-with-groups-names:~$ chgrp grp255 flag
hacker@permissions~fun-with-groups-names:~$ ls -l
total 144
drwxr-xr-x 1 hacker grp255      0 Sep 22 04:01 Desktop
-rw-r--r-- 1 root   grp255     58 Sep 23 03:45 flag
-rw-r--r-- 1 hacker grp255 142758 Sep 21 15:40 home-backup.tar.gz
hacker@permissions~fun-with-groups-names:~$ cat flag
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
```