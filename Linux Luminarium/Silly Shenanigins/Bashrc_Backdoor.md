# Silly Shenanigins

## Bashrc Backdoor
When your shell starts up, it looks for .bashrc file in your home directory and executes it as a startup script. You can customize your /home/hacker/.bashrc with useful things, such as setting environment variables, tweaking your shell configuration, and so on.

An unwitting victim's .bashrc is a common target for shenanigans. Malicious software, for example, often targets startup scripts such as .bashrc to maintain persistence into the future!

### Objective 
In this challenge, we'll pretend that you've broken into a victim user's machine! That user is named zardus, with a home directory of /home/zardus. You, as the hacker user, have write access to his .bashrc, and zardus has read-access to /flag. The victim is simulated by the script /challenge/victim, and you can launch this script at any time to observe the victim logging into the computer. Can you get the flag?

### Solve
**Flag:** `pwn.college{46DaVtuS5KWnpEX6nODE51D8pF4.QXxMTM3EDLygjN0czW}`

- First I just changed my directory to `/home/zardus` so that I can access the /.bashrc script present in it.
- Then I tried listing the files present in the directory but came up empty.
- I ran the `/challenge/victim` command to see what will be launched and displayed. Then I used `nano` command to get into the .bashrc script for the zardus user. There I simply added the `cat /flag` command at the end to get the flag since zardus already had access to the flag.
- I then again launched the `challenge/victim` command and this time when the startup .bashrc script got executed, it gave me the flag as well.

```bash
hacker@shenanigans~bashrc-backdoor:~$ cd /home/zardus
hacker@shenanigans~bashrc-backdoor:/home/zardus$ ls -l
total 0
hacker@shenanigans~bashrc-backdoor:/home/zardus$ /challenge/victim
Username: zardus
Password: **********
zardus@shenanigans~bashrc-backdoor:~$ exit
logout
hacker@shenanigans~bashrc-backdoor:/home/zardus$ nano ./.bashrc
hacker@shenanigans~bashrc-backdoor:/home/zardus$ /challenge/victim
Username: zardus
Password: **********
the flag is mine....hehehhe
pwn.college{46DaVtuS5KWnpEX6nODE51D8pF4.QXxMTM3EDLygjN0czW}
zardus@shenanigans~bashrc-backdoor:~$ exit
logout
```

### New Learnings
1. .bashrc is the startup script that gets executed whenever we start the shell. It stays in the home directory and can be customized. 
2. It also has risks that if it is changed and a malware is added to it, it will cause a security issue.