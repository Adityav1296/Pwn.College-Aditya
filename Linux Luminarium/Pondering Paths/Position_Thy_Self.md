# Pondering Paths

## Position Thy Self
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:  

```
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$
```

This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out.  
Now you can see what the ~ was in the prompt! It shows the current path that your shell is located at which is the 'home' directory.

### Objective
This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to *cd* to that directory before rerunning the challenge program.

### Solve
**Flag:** `pwn.college{02PuCN54GP6Nsr38VA2PNiyQ88J.dZDN1QDLygjN0czW}`

-> In this challenge, I first ran the command : */challenge/run* in order to get the directory where we need to go to get the flag.  
-> After getting the correct directory name in the output of the previous command, I used the *cd* command to go to that directory and re-ran the */challenge/run* command to get the flag.

```bash
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /usr/bin directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /usr/bin
hacker@paths~position-thy-self:/usr/bin$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{02PuCN54GP6Nsr38VA2PNiyQ88J.dZDN1QDLygjN0czW}
```

### New Learning
1. Using the *cd* command we can move to any available directory.
  - We can move to the root of the filesystem denoted by '/'.
  - We cannot move to the */root* directory as that is the user's home and it's access is normally blocked unless we use sudo or we are logged in as root.  

```
hacker@paths~position-thy-self:/usr/bin$ cd /
hacker@paths~position-thy-self:/$ cd /root
bash: cd: /root: Permission denied
```