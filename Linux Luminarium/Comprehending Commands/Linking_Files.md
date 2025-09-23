# Comprehending Commands 

## Finding Files
Links come in two flavors: hard and soft (also known as symbolic) links. We'll differentiate the two with an analogy:

- A hard link is when you address your apartment using multiple addresses that all lead directly to the same place (e.g., Apt 2 vs Unit 2).
- A soft link is when you move apartments and have the postal service automatically forward your mail from your old place to your new place.

In a filesystem, a file is, conceptually, an address at which the contents of that file live. A hard link is an alternate address that indexes that data --- accesses to the hard link and accesses to the original file are completely identical, in that they immediately yield the necessary data. A soft/symbolic link, instead, contains the original file name. When you access the symbolic link, Linux will realize that it is a symbolic link, read the original file name, and then (typically) automatically access that file.

Symbolic links are created with the ln command with the -s argument, like so:

```
hacker@dojo:~$ cat /tmp/myfile
This is my file!
hacker@dojo:~$ ln -s /tmp/myfile /home/hacker/ourfile
hacker@dojo:~$ cat ~/ourfile
This is my file!
hacker@dojo:~$
```

You can see that accessing the symlink results in getting the original file contents! Also, you can see the usage of ln -s. Note that the original file path comes before the link path in the command!

A symlink can be identified as such with a few methods. For example, the file command, which takes a filename and tells you what type of file it is, will recognize symlinks:

```
hacker@dojo:~$ file /tmp/myfile
/tmp/myfile: ASCII text
hacker@dojo:~$ file ~/ourfile
/home/hacker/ourfile: symbolic link to /tmp/myfile
hacker@dojo:~$
```

### Objective
This challenge the flag is hidden in a random directory on the filesystem. It's still called flag.

### Solve
**Flag:** `pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}`

-> In this challenge, I used *ln -s* command to create a symbolic link from the flag file to the not-the-flag file since the */challenge/catflag* command will only read the not-the-flag file.    

```bash
hacker@commands~linking-files:~$ ls
Desktop  flag  home-backup.tar.gz
hacker@commands~linking-files:~$ ln -s flag ~/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
```

### New Learning
1. *ln -s* command can be used to create symbolic links between 2 files. Through this, we might be able to access the contents from non-accessible files by linking them to accessible files as we did in this challenge.
