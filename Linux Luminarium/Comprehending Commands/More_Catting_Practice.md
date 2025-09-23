# Comprehending Commands 

## More Catting Practice
You can specify all sorts of paths as arguments to commands, and we'll practice some more with cat.

### Objective
In this challenge, the flag will be in some crazy directory, and I will not allow you to change directories with cd, so no cat flag for you. You must retrieve the flag by absolute path, wherever it is.

### Solve
**Flag:** `pwn.college{oloVUkLDSU-zKQOXauntz3yh7Ys.dBjM5QDLygjN0czW}`

-> In this challenge, additional info was given once I started the challenge on the terminal, in which the absolute path to the flag file was already given. So from there, I ran the *cat* command with the given absolute path as argument to it and got the flag.

```bash
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /lib/jvm/java-11-openjdk-amd64/flag. Go cat it out **without**
cding into that directory!
hacker@commands~more-catting-practice:~$ cat /lib/jvm/java-11-openjdk-amd64/flag
pwn.college{oloVUkLDSU-zKQOXauntz3yh7Ys.dBjM5QDLygjN0czW}
```