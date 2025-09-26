# Processes and Jobs

## Foregrounding Processes
you can foreground a backgrounded process with fg just like you foreground a suspended process! 

### Objective
Foreground a running background process.

### Solve
**Flag:** `pwn.college{I7xCdJ2G8k2cTXM5Ith2A-AF2d0.dhDN4QDLygjN0czW}`

- In this challenge, I first ran the `/challenge/run` command to start the run process and then sent it to backgroung using Ctrl+Z.
- Then I used `bg` command with the process name as its argument to resume it in the background.
- To bring it to the foreground again, I used the `fg` command with the process name as its argument. Once it came to the foreground, I obtained the flag.

```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$
hacker@processes~foregrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg /challenge/run
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{I7xCdJ2G8k2cTXM5Ith2A-AF2d0.dhDN4QDLygjN0czW}
```

### New Learnings
1. We can bring processes running in the background to the foreground by using the same `fg` command with the process' name as the argument.
