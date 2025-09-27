# Chaining Commands

## Scripting with Arguments
Scripts become much more powerful when they can accept arguments! This might look like:

```bash
hacker@dojo:~$ bash myscript.sh hello world
```

Here's a simple example:

```bash
hacker@dojo:~$ cat myscript.sh
#!/bin/bash
echo "First argument: $1"
echo "Second argument: $2"
hacker@dojo:~$ bash myscript.sh hello world
First argument: hello
Second argument: world
hacker@dojo:~$
```

### Objective
For this challenge, you need to write a script at /home/hacker/solve.sh that:
   1. Takes two arguments
   2. Outputs them in REVERSE order (second argument first, then the first argument)  
Once your script works correctly, run /challenge/run to get your flag!

### Solve
**Flag:** `pwn.college{8KWSp5Rfa2T0FaZkSjUPdmuuyK2.QX1MzM4EDLygjN0czW}`

- The first thing I did was to create the solve.sh file. Then I used `ls -l` command to list all its permission. Since it did not have any execution permission, I added the exection permission to the user.
- Then I used the `nano solve.sh` command to open the file and write the commands to be executed in it along with the shebang.
- Finally at the end, I added the two arguments 'pwn' and 'college' to the script using the `bash` command and then executed the script by invoking it through a relative path.
- Then ran the `/challenge/run` command to verify the output and get the flag.

```bash
hacker@chaining~scripting-with-arguments:~$ touch solve.sh
hacker@chaining~scripting-with-arguments:~$ ls -l solve.sh
-rw-r--r-- 1 hacker hacker 0 Sep 26 19:52 solve.sh
hacker@chaining~scripting-with-arguments:~$ chmod u+x solve.sh
hacker@chaining~scripting-with-arguments:~$ ls -l solve.sh
-rwxr--r-- 1 hacker hacker 0 Sep 26 19:52 solve.sh
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ bash ./solve.sh pwn college
college pwn
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here is your flag:
pwn.college{8KWSp5Rfa2T0FaZkSjUPdmuuyK2.QX1MzM4EDLygjN0czW}
```

### New Learnings
1. We can provide arguments to the scripts we write and access those arguments inside the script using special variables :
   1. $1 contains the first argument ("hello")
   2. $2 contains the second argument ("world")
   3. $3 would contain the third argument (if there had been one)...and so on
2. By providing arguments to the script to work on, we can obtain different outputs from the same script therefore making it more reusable and increasing its utility. 