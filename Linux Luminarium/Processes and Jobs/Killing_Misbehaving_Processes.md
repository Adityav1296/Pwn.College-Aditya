# Processes and Jobs

## Killing Misbehaving Processes
Sometimes, misbehaving processes can interfere with your work. These processes might need to be killed...

### Objective
In this challenge, there's a decoy process that's hogging a critical resource - a named pipe (FIFO) at /tmp/flag_fifo into which (like in the Practicing Piping FIFO challenge) /challenge/run wants to write your flag. You need to kill this process.

Your general workflow should be:

Check what processes are running.
Find /challenge/decoy in the list and figure out its process ID.
kill it.
Run /challenge/run to get the flag without being overwhelmed by decoys (you don't need to redirect its output; it'll write to the FIFO on its own).

### Solve
**Flag:** `pwn.college{gZkkO7LeNqL3p0yldCbptRLom60.QX0MzM4EDLygjN0czW}`

- In this challenge, I first ran the `ps aux` command to list all the process running. There I found the PID of the /challenge/decoy process which was 142.
- Then I used `kill` command to kill this process and ran the `/challenge/run` command. 
- During the first run, the output stalled. I interrupted the process using Ctrl+C and reran the command. This time it sent the flag to the name pipe file and I used `cat` command to extract the flag from the named pipe file.

```bash
hacker@processes~killing-misbehaving-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.7  0.0   1056   640 ?        Ss   20:09   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sle
root           7  0.3  0.0 231708  2560 ?        S    20:09   0:00 /run/dojo/bin/sleep 6h
root         137  0.0  0.0   4132  1280 ?        S    20:09   0:00 /bin/bash /challenge/.init
root         138  0.0  0.0   4132  1280 ?        S    20:09   0:00 /bin/bash /challenge/.init
root         139  0.0  0.0   5204  3520 ?        S    20:09   0:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
root         140  0.0  0.0   2744  1600 ?        S    20:09   0:00 sleep 6h
root         141  0.0  0.0   2744  1280 ?        S    20:09   0:00 sleep 6h
hacker       142  0.5  0.0  13516  9280 ?        Ss   20:09   0:00 /usr/bin/python /challenge/decoy
hacker       144  0.5  0.0 231576  3520 pts/0    Ss   20:09   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bi
hacker       150  0.0  0.0 231972  4160 pts/0    S    20:09   0:00 /run/dojo/bin/bash --login
hacker       159  0.0  0.0 233600  3840 pts/0    R+   20:09   0:00 ps aux
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.2  0.0   1056   640 ?        Ss   20:09   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sle
root           7  0.1  0.0 231708  2560 ?        S    20:09   0:00 /run/dojo/bin/sleep 6h
root         137  0.0  0.0   4132  1280 ?        S    20:09   0:00 /bin/bash /challenge/.init
root         138  0.0  0.0   4132  1280 ?        S    20:09   0:00 /bin/bash /challenge/.init
root         140  0.0  0.0   2744  1600 ?        S    20:09   0:00 sleep 6h
root         141  0.0  0.0   2744  1280 ?        S    20:09   0:00 sleep 6h
hacker       144  0.1  0.0 231576  3520 pts/0    Ss   20:09   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bi
hacker       150  0.0  0.0 231972  4160 pts/0    S    20:09   0:00 /run/dojo/bin/bash --login
hacker       160  0.0  0.0 233600  3840 pts/0    R+   20:09   0:00 ps aux
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
cat /tmp/flag_fifo
^C
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{gZkkO7LeNqL3p0yldCbptRLom60.QX0MzM4EDLygjN0czW}
```

### New Learnings
1. Some processes might misbehave and cause problems with the normally running processes. As a result, it is necessary to kill those processes.
2. We can easily identify those processes using the `ps` commands and then kill them using the `kill` command.