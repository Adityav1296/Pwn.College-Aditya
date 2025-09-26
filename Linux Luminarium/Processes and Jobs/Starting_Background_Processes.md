# Processes and Jobs

## Starting Backgrounded Processes
Of course, you don't have to suspend processes to background them: you can start them backgrounded right off the bat! It's easy; all you have to do is append a & to the command, like so:

```bash
hacker@dojo:~$ sleep 1337 &
[1] 1771
hacker@dojo:~$ ps -o user,pid,stat,cmd
USER         PID STAT CMD
hacker      1709 Ss   bash
hacker      1771 S    sleep 1337
hacker      1782 R+   ps -o user,pid,stat,cmd
hacker@dojo:~$ 
```

Here, sleep is actively running in the background, not suspended.

### Objective
Launch /challenge/run backgrounded for the flag!

### Solve
**Flag:** `pwn.college{E0hcPM7iUVNh1jokWCsClixS81y.dlDN4QDLygjN0czW}`

- In this challenge, I simply ran the `/challenge/run` command but since we need to run it in the background from the start, I added '&' at the end of the command as told in the challenge descriptiton. 

```bash
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 138
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{E0hcPM7iUVNh1jokWCsClixS81y.dlDN4QDLygjN0czW}

[1]+  Done                    /challenge/run
```

### New Learnings
1. We can start processes in the background right from the beginning. This is done by adding '&' at the end of the command.