# Pondering Paths

## Position Elsewhere
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
**Flag:** `pwn.college{AubZPnK7xom9_aOhNLL7tvKL9vI.ddDN1QDLygjN0czW}`

-> In this challenge, I first ran the command : */challenge/run* in order to get the directory where we need to go to get the flag.  
-> After getting the correct directory name in the output of the previous command, I used the *cd* command to go to that directory and re-ran the */challenge/run* command to get the flag.

```bash
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/include directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /usr/include
hacker@paths~position-elsewhere:/usr/include$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{AubZPnK7xom9_aOhNLL7tvKL9vI.ddDN1QDLygjN0czW}
```