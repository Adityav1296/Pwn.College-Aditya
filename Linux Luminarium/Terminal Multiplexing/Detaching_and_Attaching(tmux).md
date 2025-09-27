# Terminal Multiplexing

## Detaching and Attaching(tmux)
tmux (terminal multiplexer) is screen's younger, more modern cousin. It does all the same things but with some different key bindings. The biggest difference? Instead of Ctrl-A, tmux uses Ctrl-B as its command prefix.

So to detach from tmux, you press Ctrl-B followed by d.

```bash
hacker@dojo:~$ tmux
[doing some work...]
[Press Ctrl-B, then d]
[detached (from session 0)]
hacker@dojo:~$ 
```

The commands also differ: 
   1. tmux ls - List sessions
   2. tmux attach or tmux a - Reattach to session

### Objective
For this challenge:
   1. Launch tmux
   2. Detach from it.
   3. Run /challenge/run (this will send the flag to your detached session!)
   4. Reattach to see your prize

### Solve
**Flag:** `pwn.college{QauIMT73RYmFQHjjaOdnmKgQBwX.QX5gjM4EDLygjN0czW}`

- As is told in the challenge objective, I simply ran the `tmux` command to start the session. There, I intentionally performed some tasks so that when I reattach, I can confirm that it really did reattach.
- Then I deattached from the screen using Ctrl+B d. Then I ran the `/challenge/run` command to send the flag to the deattached terminal.
- Finally, I reattached to the terminal using `tmux a` command. There, I confirmed that it indeed reattached and also got the flag.

```bash
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ 11;rgb:0c0c/0c0c/0c0c
-bash: 11: command not found
-bash: rgb:0c0c/0c0c/0c0c: No such file or directory
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ echo "hello"
hello
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You will find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{QauIMT73RYmFQHjjaOdnmKgQBwX.QX5gjM4EDLygjN0czW}
Congratulations, here is your flag: pwn.college{QauIMT73RYmFQHjjaOdnmKgQBwX.QX5gjM4EDLygjN0czW}
[detached (from session 0)]
```

### New Learnings
1. Just like screen, the `tmux` command can also be used to open a terminal session inside a terminal. We can perform the tasks we want in that terminal and then deatach using Ctrl+B d.
2. It basically works just like the screen but has some differences in command prefix, listing and attaching commands.