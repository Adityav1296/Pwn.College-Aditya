# Comprehending Commands 

## Making Directories
We can create files. How about directories? You make directories using the mkdir command. Then you can stick files in there!

```
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ mkdir my_directory
hacker@dojo:/tmp$ ls
my_directory
hacker@dojo:/tmp$ cd my_directory
hacker@dojo:/tmp/my_directory$ touch my_file
hacker@dojo:/tmp/my_directory$ ls
my_file
hacker@dojo:/tmp/my_directory$ ls /tmp/my_directory/my_file
/tmp/my_directory/my_file
hacker@dojo:/tmp/my_directory$
```

### Objective
Create a /tmp/pwn directory and make a college file in it! Then run /challenge/run, which will check your solution and give you the flag!

### Solve
**Flag:** `pwn.college{0ir90qOMcyEi7hfpQcJ6Vb6MHGY.dFzM4QDLygjN0czW}`

-> In this challenge, since we need to make a directory in pwn inside the directory tmp, I first changed my directory to /tmp. There I used `mkdir pwn` to create the required directory.  
-> Now to make the college file inside pwn directory there can be two methods :
  1. We can change the directory to pwn using `cd pwn` and the use `touch college` to make the file in it.  
  2. The other method is we can directly use `touch pwn/college` from the tmp directory to create a new file inside pwn directory as has been done here.  
-> After that I ran the /challenge/run command to verify my solution and obtained the flag.  

```bash
hacker@commands~making-directories:~$ cd /tmp
hacker@commands~making-directories:/tmp$ mkdir pwn
hacker@commands~making-directories:/tmp$ ls
bin  hsperfdata_root  pwn  tmp.TpSOPGOVKK
hacker@commands~making-directories:/tmp$ touch pwn/college
hacker@commands~making-directories:/tmp$ cd pwn
hacker@commands~making-directories:/tmp/pwn$ ls
college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{0ir90qOMcyEi7hfpQcJ6Vb6MHGY.dFzM4QDLygjN0czW}
```

### New Learning
1. *mkdir* is the command used to create directories.  
2. We can create files and directories by staying in the current directory and passing the correct argument to the *touch* and *mkdir* commands.

```
hacker@commands~making-directories:~$ mkdir /tmp/pwn1
hacker@commands~making-directories:~$ cd /tmp
hacker@commands~making-directories:/tmp$ ls
bin  hsperfdata_root  pwn  pwn1  tmp.TpSOPGOVKK
```