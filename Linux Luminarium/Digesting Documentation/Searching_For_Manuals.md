# Digesting Documentation 

## Searching For Manuals
All of the manpages are gathered in a searchable database, so you'll be able to search the man page database to find the hidden challenge man page! To figure out how to search for the right manpage, read the man page manpage by doing: man man!

### Objective
This level is tricky: it hides the manpage for the challenge by randomizing its name. Though the manpage is randomly named, you still actually use /challenge/challenge to get the flag! Search for the hidden manpage that will tell you how to use /challenge/challenge.

### Solve
**Flag:** `pwn.college{EsMxcMG9H1pMTlD-5VS4On2cCya.dZTM4QDLygjN0czW}`

-> In this challenge, first I used the `man man` command to see the manual for the *man* command. From there, I found the two options that searched for a keyword through the manual pages and description of manual pages and print the name of the manual page where the match is found along with a short discription of that page.  
-> So using `man -k /challenge/challenge` I found the hidden man page for the challenge. Then I used the *man* command on that hidden page and got the option that displays the flag.

```bash
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k /challenge/challenge
sxcplncyad (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man -f /challenge/challenge
sxcplncyad (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man sxcplncyad
hacker@man~searching-for-manuals:~$ /challenge/challenge --fortune 
hacker@man~searching-for-manuals:~$ /challenge/challenge --sxcpln 915
Correct usage! Your flag: pwn.college{EsMxcMG9H1pMTlD-5VS4On2cCya.dZTM4QDLygjN0czW}
```

### New Learning
1. Each page argument given to man is normally the name of a program, utility or function. The manual page associated with each of these arguments is then found and displayed. A section, if provided, will direct man to  look only in that section of the manual. The default action is to search in all of the available sections following a pre-defined order (see DEFAULTS), and to show only the first page found, even if page exists in several sections.  
2. man -k keyword: Search the short  descriptions  and manual page names for the keyword as regular expression.  Print out any matches. Equivalent to apropos printf.  
3. man -f keyword: Lookup the manual pages referenced by keyword and print out the short descriptions of any found. Equivalent to whatis keyword.
4. Both the above commands give the list of all the man pages which match the required keyword or contain it along with a short description of those man pages.  
5. Using the *man man* command to check the manual page for *man* command.
