# Perceiving Permissions

## Executable Files
When you invoke a program, such as /challenge/run, Linux will only actually execute it if you have execute-access to the program file. Consider:

```bash
hacker@dojo:~$ ls -l /challenge/run
-rwxr-xr-x 1 root root    0 May 22 13:42 /challenge/run
hacker@dojo:~$ /challenge/run
Successfully ran the challenge!
hacker@dojo:~$
```

In this case, /challenge/run runs because it is executable by the hacker user. Because the file is owned by the root user and root group, this requires that the execute bit is set on the other permissions. If we remove these permissions, the execution will fail!

```bash
hacker@dojo:~$ chmod o-x /challenge/run
hacker@dojo:~$ ls -l /challenge/run
-rwxr-xr-- 1 root root    0 May 22 13:42 /challenge/run
hacker@dojo:~$ /challenge/run
bash: /challenge/run: Permission denied
```

### Objective 
In this challenge, the /challenge/run program will give you the flag, but you must first make it executable!

### Solve
**Flag:** `pwn.college{gwBiHtx9XjC8AMPYmTZNb-5USRc.dJTM2QDLygjN0czW}`

- In this challenge, I first changed my directory to /challenge and then listed all the files present in it along with their permissions using the `ls -l` command.
- Since the owner of the run file is the hacker already, that means we are the owner of the run file. So I just added the executable permission to the owner using the `chmod` command. I listed the files again to confirm the changes made.
- Then I executed the run program and got the flag.

```bash
hacker@permissions~executable-files:~$ cd /challenge
hacker@permissions~executable-files:/challenge$ ls -l
total 8
-rwsr-xr-x 1 root   root   1221 Jun  4 14:01 DESCRIPTION.md
-r--r--r-- 1 hacker hacker   32 Jan 14  2025 run
hacker@permissions~executable-files:/challenge$ chmod u+x run
hacker@permissions~executable-files:/challenge$ ls -l
total 8
-rwsr-xr-x 1 root   root   1221 Jun  4 14:01 DESCRIPTION.md
-r-xr--r-- 1 hacker hacker   32 Jan 14  2025 run
hacker@permissions~executable-files:/challenge$ ./run
Successful execution! Here is your flag:
pwn.college{gwBiHtx9XjC8AMPYmTZNb-5USRc.dJTM2QDLygjN0czW}
```

### New Learnings
1. We can find the details about a particular file by passing the file name to the `ls -l` command in the following way :

```bash
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r--r--r-- 1 hacker hacker 32 Jan 14  2025 /challenge/run
```