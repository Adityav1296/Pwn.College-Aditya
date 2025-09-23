# Comprehending Commands 

## Listing Files
Directories can have lots of files (and other directories) inside them. You'll need to learn to list their contents using the ls command!

ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided. Observe:

```
hacker@dojo:~$ ls /challenge
run
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ ls /home/hacker
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
```

### Objective
In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.

### Solve
**Flag:** `pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}`

-> In this challenge, I actually just ran the *ls* command in the home directory itself to see what it will list. There only I found the flag file. So I used the *cat* command on the flag file and got the flag.  
-> Then I changed my directory to */challenge* and listed the files there. There I found a this strange named file and used *cat* on it. In the output, it gave me the command *cat /flag* that I ran earlier to get the flag.

```bash
hacker@commands~listing-files:~$ ls
Desktop  flag  home-backup.tar.gz
hacker@commands~listing-files:~$ cat flag
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
hacker@commands~listing-files:~$ cd /challenge
hacker@commands~listing-files:/challenge$ ls
27838-renamed-run-23163  DESCRIPTION.md
hacker@commands~listing-files:/challenge$ cat 27838-renamed-run-23163
#!/opt/pwn.college/bash

echo "Yahaha, you found me! Here is your flag:"
cat /flag
```

### New Learning
1. *ls* command lists out the files and other directories inside the current directory. Directories are generally highlighted to mark them different from the normal files.  
2. It can also be used to list the contents of a different directory by providing the target directory as an argument to it.

```
hacker@commands~listing-files:~$ ls /challenge
27838-renamed-run-23163  DESCRIPTION.md
```