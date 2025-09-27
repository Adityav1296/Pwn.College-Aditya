# Terminal Multiplexing

## Switching Windows(tmux)
Just like screen, tmux has windows. The key combos are different, but the concept is the same. Tmux shows your windows at the bottom in a status bar that looks like:

```bash
[0] 0:bash* 1:bash
```

The * shows your current window, and each entry also shows the process that the window was created to run.

### Objective
For this challenge, We've created a tmux session with two windows:
   1. Window 0 has the flag!
   2. Window 1 has a welcome message.

Go get that flag!

### Solve
**Flag:** `pwn.college{I3MEPl9PuwAe6dxIqodqHKZYVr6.QXwkjM4EDLygjN0czW}}`

- First I listed out all the tmux sessions using the `tmux ls` command. 
- From there, I attached to the challenge_sesssion to start the challenge.
- It opened up in window 1 instead of 0 and asked to change the window to 0. Instead of directly changing to window 0 using Ctrl+B 0, I used Ctrl+B w to list out all the windows in the tmux session. From there I switched to window 0 and got the flag.

```bash
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux ls
challenge_session: 2 windows (created Sat Sep 27 08:14:42 2025)
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux a
> Excellent work! You found window 0!
> Here is your flag: pwn.college{I3MEPl9PuwAe6dxIqodqHKZYVr6.QXwkjM4EDLygjN0czW}> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{I3MEPl9PuwAe6dxIqodqHKZYVr6.QXwkjM4EDLygjN0czW}
hacker@terminal-multiplexing~switching-windows-tmux:~$
[detached (from session challenge_session)]
```

### New Learnings
1. A single tmux session can have multiple windows in it.
2. We can do various windows related tasks inside a screen terminal session using these commands :
   1. Ctrl-B c - Create a new window
   2. Ctrl-B n - Next window
   3. Ctrl-B p - Previous window
   4. Ctrl-B 0 through Ctrl-A 9 - Jump directly to window 0-9
   5. Ctrl-B w - bring up a selection menu of all of the windows

### References
1. [GeeksforGeeks : tmux command in linux](https://www.geeksforgeeks.org/linux-unix/tmux-in-linux/)