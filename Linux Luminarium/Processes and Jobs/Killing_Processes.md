# Processes and Jobs

## Killing Processes
In Linux, killing a process is done using the aggressively-named kill command. With default options, kill will terminate a process in a way that gives it a chance to get its affairs in order before ceasing to exist. You use kill to terminate it by passing the process identifier (the PID from ps) as an argument. Example :

```bash
hacker@dojo:~$ sleep 1337
hacker@dojo:~$ ps -e | grep sleep
 342 pts/0    00:00:00 sleep
hacker@dojo:~$ kill 342
hacker@dojo:~$ ps -e | grep sleep
hacker@dojo:~$
```

### Objective
In this challenge, /challenge/run will refuse to run while /challenge/dont_run is running! You must find the dont_run process and kill it. If you fail, pwn.college will disavow all knowledge of your mission.

### Solve
**Flag:** `pwn.college{kgYLY2D3MY_HSKSMv3pPACFa-3-.dJDN4QDLygjN0czW}`

- In this challenge, I first ran the `ps -ef` command and piped the output. Then I used `grep` command to find the dont_run process. 
- After that I used the `kill` command with the process ID for the dont_run process as the argument to terminate it. Then I launched the `/challenge/run` process to get the flag.

```bash
hacker@processes~killing-processes:~$ ps aux | grep dont_run
hacker       136  0.0  0.0 231576  3520 ?        Ss   19:31   0:00 /challenge/dont_run
hacker       155  0.0  0.0 230696  2560 pts/0    S+   19:31   0:00 grep --color=auto dont_run
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ ps aux | grep dont_run
hacker       157  0.0  0.0 230696  2560 pts/0    S+   19:32   0:00 grep --color=auto dont_run
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{kgYLY2D3MY_HSKSMv3pPACFa-3-.dJDN4QDLygjN0czW}
```

### New Learnings
1. As with many other commands, we can pipe the output of the `ps` command and use `grep` or other suitable commands to extract specific info from the whole list of processes.
2. `kill` command is used to terminating a running process.