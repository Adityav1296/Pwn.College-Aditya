# Terminal Multiplexing

## Finding Sessions
If you become an avid screen user, you will inevitably end up with multiple sessions running. How do you find the right one to reattach to?

Well, we can list them:

```bash
hacker@dojo:~$ screen -ls
There are screens on:
        23847.mysession   (Detached)
        23851.goodwork    (Detached)
        23855.morework    (Detached)
3 Sockets in /run/screen/S-hacker.
```

The identifiers of the sessions are the PID of each respective screen process, a dot, and the name of the screen session. To attach to a specific one, you use its name or its PID by giving it as an argument to screen -r.

```bash
hacker@dojo:~$ screen -r goodwork
```

### Objective
In this challenge, we've created three screen sessions for you. One of them contains the flag. The other two are decoys!

You'll need to check each one until you find it. Don't forget to detach (Ctrl-A d) before trying the next session!

### Solve
**Flag:** `pwn.college{g4VB-i5hwbM-dzFStn9Ok7UeibT.QX3gjM4EDLygjN0czW}`

- First I listed out all the screen sessions using the `screen -ls` command. 
- From there, I first reattached to the last session but did not find the flag. So, I deattached from that one. Then I reattached to the second session and this time I found the flag.

```bash
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        144.session_a62e554d09ec3a92    (Detached)
        147.session_3559278a1dc8f042    (Detached)
        150.session_b9adc64dd424a74c    (Detached)
3 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 150
[detached from 150.session_b9adc64dd424a74c]hacker@terminal-multiplexing~finding-sessions:~$  echo 'Wrong session! Keep looking.'
Wrong session! Keep looking.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 147
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{g4VB-i5hwbM-dzFStn9Ok7UeibT.QX3gjM4EDLygjN0czW}
pwn.college{g4VB-i5hwbM-dzFStn9Ok7UeibT.QX3gjM4EDLygjN0czW}
[detached from 147.session_3559278a1dc8f042]
```

### New Learnings
1. We can create multiple sessions in the same window using the `screen -S session_name` command. 
2. We use the `screen -ls` command to list the active and deattached sessions.
3. Using `screen -r session_name/session_id` we can reattach to a particular session and continue our work there.

### Reference 
1. [GeeksforGeeks : Using screen command in linux](https://www.geeksforgeeks.org/linux-unix/screen-command-in-linux-with-examples/)