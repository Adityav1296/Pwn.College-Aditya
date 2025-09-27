# Terminal Multiplexing

## Detaching and Attaching
Imagine you're working on something important over a remote connection, and your connection drops. With a normal terminal (outside of this awesome dojo environment), everything's gone. With screen, your work keeps running, and you can reattach later!

You can also detach on purpose, which we'll do in this challenge. You detach by pressing Ctrl-A, followed by d (for detach). This leaves your session running in the background while you return to your normal terminal.

```bash
hacker@dojo:~$ screen
[doing some work...]
[Press Ctrl-A, then d]
[detached from 12345.pts-0.hostname]
hacker@dojo:~$ 
```

To reattach, you can use the -r argument to screen:

```bash
hacker@dojo:~$ screen -r
```

### Objective
For this challenge, you'll need to:
   1. Launch screen
   2. Detach from it.
   3. Run /challenge/run (this will secretly send the flag to your detached session!)
   4. Reattach to see your prize

### Solve
**Flag:** `pwn.college{0HmeCpSD7m8lsTSEYcHpmLLgh8W.QX2gjM4EDLygjN0czW}`

- As is told in the challenge objective, I simply ran the `screen` command and started a screen session. There, I intentionally performed some tasks so that when I reattach, I can confirm that it really did reattach.
- Then I deattached from the screen using Ctrl+A and then pressing d to deattach. Then I ran the `/challenge/run` command to send the flag to the deattached screen.
- Finally, I reattached to the screen using `screen -r` command. There, I confirmed that it indeed reattached and also got the flag.

```bash
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo "hello"
hello
hacker@terminal-multiplexing~detaching-and-attaching:~$ ls
Desktop  flag  home-backup.tar.gz  solve.sh
hacker@terminal-multiplexing~detaching-and-attaching:~$ cat solve.sh
#!/bin/bash

if [ "$1" == "pwn" ];
then
   echo "college";
elif [ "$1" == "hack" ]
then
   echo "the planet"
elif [ "$1" == "learn" ]
then
   echo "linux"
else
   echo "unknown"
fi
[detached from 154.pts-1.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 154.pts-1.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You will find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{0HmeCpSD7m8lsTSEYcHpmLLgh8W.QX2gjM4EDLygjN0czW}
Yes! Flag is: pwn.college{0HmeCpSD7m8lsTSEYcHpmLLgh8W.QX2gjM4EDLygjN0czW}
[screen is terminating]
```

### New Learnings
1. We can deattach from a screen using Ctrl+A and then pressing d. That way, the work we were doing in that screen terminal will keep running instead of getting lost. 
2. Then, in order to reattach, we use the `screen -r` command and get back to the work we left running.
3. Ctrl-A is screen's activation key for all of its shortcuts in its default configuration. All screen functionality is activated by some command combination starting with Ctrl-A.