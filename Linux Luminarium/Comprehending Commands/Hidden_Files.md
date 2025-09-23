# Comprehending Commands 

## Hidden Files
Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag, as so:

```
hacker@dojo:~$ touch pwn
hacker@dojo:~$ touch .college
hacker@dojo:~$ ls
pwn
hacker@dojo:~$ ls -a
.college	pwn
hacker@dojo:~$
```

### Objective
This challenge wants you to find the flag, hidden as a dot-prepended file in /.

### Solve
**Flag:** `pwn.college{ENUHPf4mZQZBpuXOkmVelFdBbnZ.dBTN4QDLygjN0czW}`

-> In this challenge, I initially used the *ls -a* command in the home directory to check how it works and listed the hidden files that can be found in the home directory.  
-> Then I changed my directory to root(/) and used both *ls* and *ls -a* commands there to see the difference between the two of them.  
-> By using *ls -a* command, I found the hidden flag file. Then I used *cat* command on that hidden file to obtain the flag.  

```bash
hacker@commands~hidden-files:~$ ls
Desktop  flag  home-backup.tar.gz
hacker@commands~hidden-files:~$ ls -a
.   .ICEauthority  .cache   .local   flag
..  .bash_history  .config  Desktop  home-backup.tar.gz
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls
bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ ls -a
.                    bin        etc    lib64   nix   run   tmp
..                   boot       home   libx32  opt   sbin  usr
.dockerenv           challenge  lib    media   proc  srv   var
.flag-2463329611992  dev        lib32  mnt     root  sys
hacker@commands~hidden-files:/$ cat .flag-2463329611992
pwn.college{ENUHPf4mZQZBpuXOkmVelFdBbnZ.dBTN4QDLygjN0czW}
```

### New Learning
1. *ls -a* command displays the hidden files that are not displayed by simply running the *ls* command. Hidden files here can include files beginning with '.' or '..'