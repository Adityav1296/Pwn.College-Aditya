# Terminal Multiplexing

## Switching Windows
screen is just a weird sort of terminal-with-a-terminal. But it can be much more!

Inside a single screen session, you can have multiple windows, like your browser has multiple tabs. This can be super handy for organizing different tasks!

### Objective
For this challenge, we've set up a screen session with two windows:
   1. Window 0 has... well, you'll have to switch there to find out!
   2. Window 1 has a welcome message

Attach to the session with screen -r, then use one of the key combinations above to switch to Window 1. Go get that flag!

### Solve
**Flag:** `pwn.college{8ku-muFsMIsJX6CtD0zYc_Is8aO.QX4gjM4EDLygjN0czW}`

- First I listed out all the screen sessions using the `screen -ls` command. 
- From there, I reattached to the challenge_sesssion to start the challenge.
- It opened up in window 1 instead of 0 and asked to change the window to 0. So, I used Ctrl+A 0 to change to window 0 and got the flag.

```bash
hacker@terminal-multiplexing~switching-windows:~$ screen -ls
There are screens on:
        144.session_a62e554d09ec3a92    (Remote or dead)
        147.session_3559278a1dc8f042    (Remote or dead)
        150.session_b9adc64dd424a74c    (Remote or dead)
        135.challenge_session   (Detached)
4 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~switching-windows:~$ screen -r 135
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Welcome to the window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-A 0 to switch to window 0!
> MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{8ku-muFsMIsJX6CtD0zYc_Is8aO.QX4gjM4EDLygjN0czW}> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{8ku-muFsMIsJX6CtD0zYc_Is8aO.QX4gjM4EDLygjN0czW}
hacker@terminal-multiplexing~switching-windows:~$
[detached from 135.challenge_session]
```

### New Learnings
1. A single screen terminal session can have many windows inside it with each window running different programs and scripts and works.
2. We can do various windows related tasks inside a screen terminal session using these commands :
   1. Ctrl-A c - Create a new window
   2. Ctrl-A n - Next window
   3. Ctrl-A p - Previous window
   4. Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9
   5. Ctrl-A " - bring up a selection menu of all of the windows