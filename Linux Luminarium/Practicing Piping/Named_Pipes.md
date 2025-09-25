# Practicing Piping

## Named Pipes 
You can also create your own persistent named pipes that stick around on the filesystem! These are called FIFOs, which stands for First (byte) In, First (byte) Out.

You create a FIFO using the mkfifo command:

```bash
hacker@dojo:~$ mkfifo my_pipe
hacker@dojo:~$ ls -l my_pipe
prw-r--r-- 1 hacker hacker 0 Jan 1 12:00 my_pipe
-rw-r--r-- 1 hacker hacker 0 Jan 1 12:00 some_file
hacker@dojo:~$
```

Notice the p at the beginning of the permissions - that indicates it's a pipe! That's markedly different than the - that's at the beginning of normal files. Unlike the automatic named pipes from process substitution:

  1. You control where FIFOs are created
  2. They persist until you delete them
  3. Any process can write to them by path (e.g., echo hi > my_pipe)
  4. You can see them with ls and examine them like files

One problem with FIFOs is that they'll "block" any operations on them until both the read side of the pipe and the write side of the pipe are ready.

```bash
hacker@dojo:~$ mkfifo myfifo
hacker@dojo:~$ echo pwn > myfifo
hacker@dojo:~$ cat myfifo
pwn
hacker@dojo:~$
```

When we ran cat myfifo, the pipe had both sides of the connection all set, and unblocked, allowing echo pwn > myfifo to run, which sent pwn into the pipe, where it was read by cat.

### Objective 
This challenge will be a simple introduction to FIFOs. You'll need to create a /tmp/flag_fifo file and redirect the stdout of /challenge/run to it. If you're successful, /challenge/run will write the flag into the FIFO! Go do it!

### Solve
**Flag:** `pwn.college{8X_9AHtipMMJpBeYjhy7j4uArO7.QXzMzM4EDLygjN0czW}`

- In this challenge, initially I thought that the processes can work separately. That we can type `/challenge/run > /tmp/flag_fifo` command one time and then on the next one we can type `cat /tmp/flag_fifo`. But that did not work out.
- So I used the pipe operator to link them together and obtained the flag. 

```bash
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You are successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo!
Bash will now try to open the FIFO for writing, to pass it as the stdout of
/challenge/run. Recall that operations on FIFOs will *block* until both the
read side and the write side is open, so /challenge/run will not actually be
launched until you start reading from the FIFO!
^C
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
^C
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo | cat /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo!
Bash will now try to open the FIFO for writing, to pass it as the stdout of
/challenge/run. Recall that operations on FIFOs will *block* until both the
read side and the write side is open, so /challenge/run will not actually be
launched until you start reading from the FIFO!
You've correctly redirected /challenge/run's stdout to a FIFO at
/tmp/flag_fifo! Here is your flag:
pwn.college{8X_9AHtipMMJpBeYjhy7j4uArO7.QXzMzM4EDLygjN0czW}
```

### New Learnings
1. No disk storage: FIFOs pass data directly between processes in memory - nothing is saved to disk
2. Ephemeral data: Once data is read from a FIFO, it's gone (unlike files where data persists)
3. Automatic synchronization: Writers block until the readers are ready, and vice-versa. This is actually useful! It provides automatic synchronization. Consider the example above: with a FIFO, it doesn't matter if cat myfifo or echo pwn > myfifo is executed first; each would just wait for the other. With files, you need to make sure to execute the writer before the reader.
4. Complex data flows: FIFOs are useful for facilitating complex data flows, merging and splitting data in flexible ways, and so on. For example, FIFOs support multiple readers and writers.
