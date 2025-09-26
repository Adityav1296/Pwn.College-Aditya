# Untangling Users

## Cracking Passwords
When you enter a password for su, it compares it against the stored password for that user. These passwords used to be stored in /etc/passwd, but because /etc/passwd is a globally-readable file, this is not good for passwords, these were moved to /etc/shadow. Here is the example /etc/shadow from the previous level:

```
root:$6$s74oZg/4.RnUvwo2$hRmCHZ9rxX56BbjnXcxa0MdOsW2moiW8qcAl/Aoc7NEuXl2DmJXPi3gLp7hmyloQvRhjXJ.wjqJ7PprVKLDtg/:19921:0:99999:7:::
daemon:*:19873:0:99999:7:::
bin:*:19873:0:99999:7:::
sys:*:19873:0:99999:7:::
sync:*:19873:0:99999:7:::
systemd-resolve:*:19901:0:99999:7:::
mysql:!:19901:0:99999:7:::
messagebus:*:19901:0:99999:7:::
sshd:*:19901:0:99999:7:::
hacker::19916:0:99999:7:::
zardus:$6$bEFkpM0w/6J0n979$47ksu/JE5QK6hSeB7mmuvJyY05wVypMhMMnEPTIddNUb5R9KXgNTYRTm75VOu1oRLGLbAql3ylkVa5ExuPov1.:19921:0:99999:7:::
```

Separated by :s, the first field of each line is the username and the second is the password. A value of * or ! functionally means that password login for the account is disabled, a blank field means that there is no password. the long string such as Zardus' password is the result of one-way-encrypting (hashing) Zardus' password from the last level. 

When you input a password into su, it one-way-encrypts (hashes) it and compares the result against the stored value. If the result matches, su grants you access to the user! 

If you have the hashed value of the password, you can crack it! The cracking can be done via the famous John the Ripper, as so:

```bash
hacker@dojo:~$ john ./my-leaked-shadow-file
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Will run 32 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
password1337      (zardus)
1g 0:00:00:22 3/3 0.04528g/s 10509p/s 10509c/s 10509C/s lykys..lank
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@dojo:~$
```

### Objective
This level simulates this story, giving you a leak of /etc/shadow (in /challenge/shadow-leak). Crack it (this could take a few minutes), su to zardus, and run /challenge/run to get the flag!

### Solve
**Flag:** `pwn.college{gVGpCjQkBNMWkS0iM7T84tzyT_a.ddTN0UDLygjN0czW}`

- First I changed my directory to /challenge. Then I listed the files present in the directory using `ls` command.
- Then using the command `john` on the shadow-leak file, I cracked the hashed password stored in it. And then listed them using the `john --show` command with the file as an argument to the command.
- From there, I got the password to the zardus user account. Using `su` I then changed the user to zardus and logged in using the cracked password I got. Then I ran the `/challenge/run` command to get the flag.

```bash
hacker@users~cracking-passwords:~$ cd /challenge
hacker@users~cracking-passwords:/challenge$ ls
DESCRIPTION.md  bin  run  shadow-leak
hacker@users~cracking-passwords:/challenge$ john shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:07 76% 1/3 0g/s 287.5p/s 287.5c/s 287.5C/s 9999945..Z9999932
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04916g/s 286.2p/s 286.2c/s 286.2C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:/challenge$ john --show
Password files required, but none specified
hacker@users~cracking-passwords:/challenge$ john --show ./shadow-leak
hacker:NO PASSWORD:20338:0:99999:7:::
zardus:aardvark:20357:0:99999:7:::

2 password hashes cracked, 0 left
hacker@users~cracking-passwords:/challenge$ su zardus
Password:
zardus@users~cracking-passwords:/challenge$ whoami
zardus
zardus@users~cracking-passwords:/challenge$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{gVGpCjQkBNMWkS0iM7T84tzyT_a.ddTN0UDLygjN0czW}
```

### New Learnings
1. John the Ripper is the name of the process through which we can crack the hashed passwords in the /etc/shadow files. We use the command `john file_name` for this purpose.
2. The /etc/shadow files are generally readable only to the root user, the leaked backup files can be read by anyone. 