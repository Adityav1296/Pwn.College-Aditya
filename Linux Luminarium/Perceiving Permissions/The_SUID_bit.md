# Perceiving Permissions

## The SUID Bit
the "Set User ID" (SUID) permissions bit allows the user to run a program as the owner of that program's file.

This is actually the exact mechanism used to let the challenge programs you run read the flag or, outside of pwn.college, to enable system administration tools such as su, sudo, and so on. The permissions of a file with SUID look like this:

```bash
hacker@dojo:~$ ls -l /usr/bin/sudo
-rwsr-xr-x 1 root root 232416 Dec 1 11:45 /usr/bin/sudo
hacker@dojo:~$
```

The s part in place of the executable bit means that the program is executable with SUID. It means that, regardless of what user runs the program the program will execute as the owner user.

As the owner of a file, you can set a file's SUID bit by using chmod:

```bash
chmod u+s [program]
```

### Objective 
Now, we are going to let you add the SUID bit to the /challenge/getroot program in order to spawn a root shell for you to cat the flag yourself!

### Solve
**Flag:** `pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}`

- I first listed the permissions of /challenge/getroot using the `ls -l` command. Then I added the SUID bit 's' to the user in place of the execution bit of the user. To confirm it, I again listed the permissions of the file this time containing the SUID bit.
- Then I ran the /challenge/getroot command and opened the root shell. There also, I listed the permissions of the flag file to make sure it was readable. 
- Once confirmed, I used `cat` to read the flag.

```bash
hacker@permissions~the-suid-bit:~$ ls -l /challenge/getroot
-rwxr-xr-x 1 root root 155 Jan 14  2025 /challenge/getroot
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ ls -l /challenge/getroot
-rwsr-xr-x 1 root root 155 Jan 14  2025 /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# ls -l flag
-rwxr--r-- 1 root root 58 Sep 23 03:45 flag
root@permissions~the-suid-bit:~# cat flag
pwn.college{4Euzpsea2ACCmgGGIBfrG07PuF9.dFzN1QDLygjN0czW}
root@permissions~the-suid-bit:~# exit
exit
hacker@permissions~the-suid-bit:~$
```

### New Learnings
1. We can set the SUID bit for a file in place of the execution bit of the user. This bit can only be set by the owner of the file. 
2. When a user executes a file or command with the SUID bit set in it, it will run with the privileges of the file or command owner. 