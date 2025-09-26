# Processes and Jobs

## Backgrounding Processes
You've resumed processes in the foreground with the fg command. You can also resume processes in the background with the bg command! This will allow the process to keep running, while giving you your shell back to invoke more commands in the meantime.

### Objective
This level's run wants to see another copy of itself running, not suspended, and using the same terminal. How? Use the terminal to launch it, then suspend it, then background it with bg and launch another copy while the first is running in the background!

### Solve
**Flag:** `pwn.college{Iuu_navUDZU7IsQtZykqBnpF6Ip.ddDN4QDLygjN0czW}`

- In this challenge, I first ran the `/challenge/run` command to start the run process and then sent it to backgroung using Ctrl+Z.
- Then I used `bg` command with the process name as its argument to resume it in the background.

```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         138 S+   bash /challenge/run
root         140 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         138 S    bash /challenge/run
root         148 S    sleep 6h
root         149 S+   bash /challenge/run
root         151 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{Iuu_navUDZU7IsQtZykqBnpF6Ip.ddDN4QDLygjN0czW}
```

### New Learnings
1. We can resume the background processes using the `bg` command. It takes the process' name as its argument and resumes it in the background.
2. T means that the process is suspended due to our Ctrl-Z. The S in bash's STAT column means that bash is sleeping while waiting for input. The R in ps's column means that it's actively running, and the + means that it's in the foreground!

```bash
hacker@dojo:~$ ps -o user,pid,stat,cmd
USER         PID STAT CMD
hacker       702 Ss   bash
hacker       762 T    sleep 1337
hacker       782 R+   ps -o user,pid,stat,cmd
hacker@dojo:~$ 
```

Watch what happens when we resume sleep in the background:

```bash
hacker@dojo:~$ bg
[1]+ sleep 1337 &
hacker@dojo:~$ ps -o user,pid,stat,cmd
USER         PID STAT CMD
hacker       702 Ss   bash
hacker       762 S    sleep 1337
hacker      1224 R+   ps -o user,pid,stat,cmd
hacker@dojo:~$
```

Boom! The sleep now has an S. It's sleeping while, well, sleeping, but it's not suspended! It's also in the background and thus doesn't have the +.
