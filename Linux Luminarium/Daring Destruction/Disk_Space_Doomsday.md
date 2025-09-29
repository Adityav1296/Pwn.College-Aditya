# Daring Destruction

## Disk-Space Doomsday
The available space in /home/hacker in this container is a measly 1 gigabyte. In this level you will clog up /home/hacker with so much junk that even a tiny 1 megabyte file can't be created. When this happens, your workspace becomes unusable.

How to fill the disk? There are so many ways. Here, we'll teach you the yes command! The yes outputs y over and over forever. The typical usage is to automate confirmation prompts ("Are you sure you want to delete this file?") using piping, but we'll use it here to make a massive file full of "y" lines. Just redirect yes to a file in your home directory, and you'll fill your disk in a minute or two!

### Objective
This challenge forces you to fill the disk and then clean up. The process:
   1. Fill your disk.
   2. Run /challenge/check. It will attempt to create a 1 megabyte temporary file. If that fails, you pass the first stage and the checker will ask you to free the space.
   3. Delete the file you made (with rm) to clear up the space.
   4. Run /challenge/check a second time. If it can now create the temporary file (i.e., you successfully cleaned up your home directory), you’ll receive the flag.

### Solve
**Flag:** `pwn.college{cXEg8K9LJVz-XSWkUGjpH8Mzzpf.QXyITM3EDLygjN0czW}`

- In this challenge, I simply made a file named cleanup and the redirected the output of the yes command to it in order to fill up the disk space.
- Then I ran the `/challenge/check` command to check if the disk is filled. Once confirmed, I then removed the cleanup file to empty the space. 
- Then I ran the `/challenge/check` command again and got the flag.

```bash
hacker@destruction~disk-space-doomsday:~$ touch cleanup
hacker@destruction~disk-space-doomsday:~$ ls
Desktop  bin  cleanup  flag  home-backup.tar.gz
hacker@destruction~disk-space-doomsday:~$ yes | cleanup
bash: cleanup: command not found
yes: standard output: Broken pipe
hacker@destruction~disk-space-doomsday:~$ yes > cleanup
yes: standard output: Disk quota exceeded
hacker@destruction~disk-space-doomsday:~$ /challenge/check
Well done, you clogged the disk. Now free that space (remove the file you created) and run /challenge/check again to prove you cleaned up!
hacker@destruction~disk-space-doomsday:~$ rm cleanup
hacker@destruction~disk-space-doomsday:~$ /challenge/check
Disk space restored. Here is your flag:
pwn.college{cXEg8K9LJVz-XSWkUGjpH8Mzzpf.QXyITM3EDLygjN0czW}
```

### New Learnings
1. The yes outputs y over and over forever. As a result it can easily fill up the disk space if we mistakenly redirect it to a file in our disk. So that should be avoided.
2. It can be used to automate confirmation.