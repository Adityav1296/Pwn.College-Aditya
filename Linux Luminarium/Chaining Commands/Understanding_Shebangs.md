# Chaining Commands

## Understanding Shebangs
Your shellscripts can only be launched from the shell. This won't work if your script was being invoked by, say, a program written in Python.

When a program is invoked in Linux, the Linux kernel first inspects the file to determine how it should be run. This does NOT use the extension (which is why you don't have to name your shell scripts with a .sh extension, or your Python scripts with a .py extension, or so on). Rather, Linux looks at the first few bytes of the file for this information.

There are a bunch of different types of programs, but if the program file starts with the characters #! (often termed a "shebang"), Linux treats the file as an interpreted program, and the contents of the rest of the line as the path to the interpreter. It then invokes the interpreter with the path to the program file as its only argument.

Consider this shell script:

```bash
#!/bin/bash
echo "Hello Hackers!"
```

This can be executed as:

```bash
hacker@dojo:~$ chmod a+x script.sh
hacker@dojo:~$ ./script.sh
Hello Hackers!
hacker@dojo:~$
```

When ./script.sh was executed, Linux opened the file, read the first line, extracted /bin/bash as the interpreter, and executed /bin/bash ./script.sh to launch the script!

Note, the shebang line must be the VERY FIRST line of the file - no blank lines or spaces before it!

### Objective
For this challenge, create a script at /home/hacker/solve.sh that has a proper shebang and outputs "hack the planet". Remember to make it executable, then run /challenge/run to verify your script works correctly!

### Solve
**Flag:** `pwn.college{E1jN7YHEK-Uvniq7_GTY5oBEjIA.QX5MzM4EDLygjN0czW}`

- The first thing I did was to create the solve.sh file. Then I used `ls -l` command to list all its permission. Since it did not have any execution permission, I added the exection permission to the user.
- Then I used the `nano solve.sh` command to open the file and write the commands to be executed in it along with the shebang.
- Finally at the end, I simply executed the script by invoking it through a relative path and then ran the `/challenge/run` command to verify the output and get the flag.

```bash
hacker@chaining~understanding-shebangs:~$ touch solve.sh
hacker@chaining~understanding-shebangs:~$ ls -l solve.sh
-rw-r--r-- 1 hacker hacker 0 Sep 26 19:52 solve.sh
hacker@chaining~understanding-shebangs:~$ chmod u+x solve.sh
hacker@chaining~understanding-shebangs:~$ ls -l solve.sh
-rwxr--r-- 1 hacker hacker 0 Sep 26 19:52 solve.sh
hacker@chaining~understanding-shebangs:~$ nano solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{E1jN7YHEK-Uvniq7_GTY5oBEjIA.QX5MzM4EDLygjN0czW}
```

### New Learnings
1. The scripts we write can't always be invoked through the bash shell. Sometimes the scripts might be in some other progamming language and the shell will not interpret it by its extension type. As a result, the script won't be executed.
2. To solve this, we use shebangs starting with `#!`. These are used to specify the interpreter needed to interpret the script. The shell reads these first few bytes of the file and understands that the file is of interpreted programs and then passes its content to the specified interpreter. 
3. Common shebangs you might see:
    1. #!/bin/bash for bash scripts
    2. #!/usr/bin/python3 for Python scripts
    3. #!/bin/sh for POSIX shell scripts --- this is a more primitive predecessor to bash with fewer features, but more compatibility to non-Linux systems!