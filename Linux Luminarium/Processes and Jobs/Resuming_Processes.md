# Processes and Jobs

## Resuming Processes
Usually, when you suspend processes, you'll want to resume them at some point. Otherwise, why not just terminate them? To resume processes, your shell provides the fg command, a builtin that takes the suspended process, resumes it, and puts it back in the foreground of your terminal.

### Objective
This challenge's run needs you to suspend it, then resume it. Good luck!

### Solve
**Flag:** `pwn.college{EWjqWvtH0BcFKd7ibCKvzTdJgzT.dZDN4QDLygjN0czW}`

- In this challenge, I first ran the `/challenge/run` command to start the run process and then sent it to backgroung using Ctrl+Z.
- Then I used `fg` command with the process name as its argument to bring it back to the foreground.

```bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{EWjqWvtH0BcFKd7ibCKvzTdJgzT.dZDN4QDLygjN0czW}
Don't forget to press Enter to quit me!

Goodbye!
```

### New Learnings
1. We can bring background processes to the foreground using the `fg` command. This command does not take the PID as its argument.