# Daring Destruction

## Finding Meaning After rm -rf /
So you can live without cat! How about without ls? This time, /challenge/check will restore the flag to a randomly-named file. You'll need to find it without reaching for your ls command.

There are a lot of ways to solve this challenge. echo is a builtin, and you can File Glob an argument to it to expand to all files! For example, echo * will print out the names of all of the files in the current directory. Similarly, you can use tab-completion (hit tab a few times) of an argument to have the shell list possible files for you.

### Objective
In this challenge, whatever route you use, find the randomly-named file that /challenge/check makes in / after you rm, read it, and get the flag!

### Solve
**Flag:** `pwn.college{gOGmPqu729IjlQj0r7qV0_D4Cp_.QX0MTM3EDLygjN0czW}`

- In this challenge, I simply ran the /challenge/check command in the background and once it started, I used `rm --no-preserve-root -rf /` command to wipe out the entire disk. 
- Then I changed the directory to '/' and double tapped TAB. It listed all the commands present I think. So obviously none of them worked when I tried to read them. 
- Then I used `echo /` and double tapped TAB. This time it listed the files present there. Then I read the random file and displayed its content on the terminal.

```bash
hacker@destruction~finding-meaning-after-rm-rf-:~$ /challenge/check &
[1] 142
hacker@destruction~finding-meaning-after-rm-rf-:~$ Looks like you haven't wiped the system! We'll check again in 5 seconds...
rm -Looks like you haven't wiped the system! We'll check again in 5 seconds...
rm --no-prLooks like you haven't wiped the system! We'll check again in 5 sehacker@destruction~finding-meaning-after-rm-rf-:~$  rm --no-preserve-root -rfm --no-preserve-root -rf
bash: rrm: command not found
hacker@destruction~finding-meaning-after-rm-rf-:~$ Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll checrm --no-preserve-root -rf
hacker@destruction~finding-meaning-after-rm-rf-:~$ Looks like you haven't wiped the system! We'll check again in 5 seconds...

hacker@destruction~finding-meaning-after-rm-rf-:~$ rm --no-preserve-root -rfLooks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll checrm --no-preserve-root -rfrm --no-preserve-root -rf /
/bin/rm: invalid option -- 'm'
Try '/bin/rm --help' for more information.
hacker@destruction~finding-meaning-after-rm-rf-:~$ Looks like you haven't wiped the system! We'll check again in 5 seconds...
rm --no-preserve-root -rf /Looks like you haven't wiped the system! We'll chhacker@destruction~finding-meaning-after-rm-rf-:~$ rm --no-preserve-root -rf /

Looks like you haven't wiped the system! We'll check again in 5 seconds...
/bin/rm: cannot remove '/etc/hosts': Device or resource busy
/bin/rm: cannot remove '/etc/resolv.conf': Device or resource busy
/bin/rm: cannot remove '/etc/hostname': Device or resource busy
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
/bin/rm: cannot remove '/usr/sbin/docker-init': Device or resource busy
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
/bin/rm: skipping '/sys', since it's on a different device
/bin/rm: skipping '/home/hacker', since it's on a different device
/bin/rm: skipping '/run/dojo/sys', since it's on a different device
/bin/rm: skipping '/proc', since it's on a different device
/bin/rm: skipping '/dev', since it's on a different device
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
/bin/rm: skipping '/nix', since it's on a different device
hacker@destruction~finding-meaning-after-rm-rf-:~$
hacker@destruction~finding-meaning-after-rm-rf-:~$ YES! You did it again! Go read the flag!

[1]+  Done                    /challenge/check
hacker@destruction~finding-meaning-after-rm-rf-:~$ cd /
hacker@destruction~finding-meaning-after-rm-rf-:/$
!            continue     fc           mapfile      times
./           coproc       fg           popd         trap
:            declare      fi           printf       true
[            dirs         for          pushd        type
[[           disown       function     pwd          typeset
]]           do           getopts      read         ulimit
alias        docker-init  grep         readarray    umask
bg           done         hash         readonly     unalias
bind         echo         help         return       unset
break        elif         history      select       until
builtin      else         if           set          wait
caller       enable       in           shift        while
case         esac         jobs         shopt        {
cd           eval         kill         source       }
command      exec         let          suspend
compgen      exit         local        test
complete     export       logout       then
compopt      false        ls           time
hacker@destruction~finding-meaning-after-rm-rf-:/$
hacker@destruction~finding-meaning-after-rm-rf-:/$ read h < false
bash: false: No such file or directory
hacker@destruction~finding-meaning-after-rm-rf-:/$ read h < true
bash: true: No such file or directory
hacker@destruction~finding-meaning-after-rm-rf-:/$ read h < unset
bash: unset: No such file or directory
hacker@destruction~finding-meaning-after-rm-rf-:/$ read h < wait
bash: wait: No such file or directory
hacker@destruction~finding-meaning-after-rm-rf-:/$ wait
hacker@destruction~finding-meaning-after-rm-rf-:/$ while
> dd^C
hacker@destruction~finding-meaning-after-rm-rf-:/$ type
hacker@destruction~finding-meaning-after-rm-rf-:/$ echo /
c0d7703d  etc/      nix/      run/      usr/
dev/      home/     proc/     sys/
hacker@destruction~finding-meaning-after-rm-rf-:/$ read h < c0d7703d
hacker@destruction~finding-meaning-after-rm-rf-:/$ echo "$h"
pwn.college{gOGmPqu729IjlQj0r7qV0_D4Cp_.QX0MTM3EDLygjN0czW}
```

### New Learnings
1. We can use commands like `echo /` or `echo *` to list all the files present after wiping the whole system. They work since echo is a shell builtin command. Then we can use `read` command to read the contents on the files and echo them onto the terminal.