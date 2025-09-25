# Shell Variables

## Printing Exported Variables
There are multiple ways to access variables in bash. echo was just one of them, and we'll now learn at least one more in this challenge.

### Objective 
Try the env command: it'll print out every exported variable set in your shell, and you can look through that output to find the FLAG variable!

### Solve
**Flag:** `pwn.college{U8VhYxjUbqa8pr-iOmADpxcPLfr.dhTN1QDLygjN0czW}`

- In this challenge, first I created a child shell using *sh* command.
- There, I ran the *env* command to print the environment variables and obtain the flag from the list.
- Just to try, I piped the output of the *env* command and then used *grep* command on it to directly get the flag.
- I also ran the env command in the main shell and it still displayed all the environment variables.

```bash
hacker@variables~printing-exported-variables:~$ sh
sh-5.2$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
_=/run/dojo/bin/env
DOJO_AUTH_TOKEN=d0726a35799a0f8f0ffcd63a4d50a93bb77b63ada8d957561b0fcc63d35cb2f6
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{U8VhYxjUbqa8pr-iOmADpxcPLfr.dhTN1QDLygjN0czW}
TERM=xterm-256color
TERMINFO=/run/dojo/share/terminfo
SHLVL=3
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
sh-5.2$ env | grep pwn.college
FLAG=pwn.college{U8VhYxjUbqa8pr-iOmADpxcPLfr.dhTN1QDLygjN0czW}
sh-5.2$ exit
exit
```

### New Learnings
1. To list out all the environment variables, we can use *env* command. We can use the *grep* command along with it to find a particular variable.