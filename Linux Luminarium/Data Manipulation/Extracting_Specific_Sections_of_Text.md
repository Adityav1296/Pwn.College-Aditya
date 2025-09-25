# Data Manipulation

## Extracting Specific Sections of Text
Sometimes, you want to grab specific columns of data, such as the first column, the third column, or the 42nd column. For this, there's the cut command. For example, imagine that you have the following data file:

```bash
hacker@dojo:~$ cat scores.txt
hacker 78 99 67
root 92 43 89
hacker@dojo:~$
```

You could use cut to extract specific columns:

```bash
hacker@dojo:~$ cut -d " " -f 1 scores.txt
hacker
root
hacker@dojo:~$ cut -d " " -f 2 scores.txt
78
92
hacker@dojo:~$ cut -d " " -f 3 scores.txt
99
43
hacker@dojo:~$
```

The -d argument specifies the column delimiter (how columns are separated). In this case, it's a space character. Of course, it has to be in quotes here so that the shell knows that the space is an argument rather than a space separating other arguments! The -f argument specifies the field number (which column to extract).

### Objective
In this challenge, the /challenge/run program will give you a bunch of lines with random numbers and single characters (characters of the flag) as columns. Use cut to extract the flag characters, then pipe them to tr -d to join them together into a single line. 

### Solve
**Flag:** `pwn.college{IHCtX6E6A4ynCbEBIeY753t_UpS.QX3ETM3EDLygjN0czW}`

- In this challenge, I first ran the /challenge/run command to just check and find the number of column in which the flag characters were.
- Then, using the piping operator, I piped this output to the *cut* command where I picked all the characters of the flag.
- I further piped the second output to the *tr -d* command and remove newlines from it to get the flag.

```bash
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run
9063 p
32238 w
5940 n
30401 .
9217 c
31930 o
18204 l
9282 l
30870 e
27365 g
25755 e
1424 {
13874 I
9904 H
29194 C
8464 t
18860 X
15946 6
4030 E
7613 6
4006 A
803 4
263 y
4992 n
30741 C
22982 b
31284 E
29801 B
22542 I
9161 e
30451 Y
22938 7
20053 5
22949 3
28132 t
13904 _
15963 U
26081 p
19483 S
910 .
26209 Q
6890 X
12217 3
13682 E
29279 T
17434 M
15422 3
18633 E
14418 D
20573 L
16722 y
8046 g
3057 j
4673 N
10847 0
19407 c
13931 z
14561 W
20683 }
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d '\n'
pwn.college{IHCtX6E6A4ynCbEBIeY753t_UpS.QX3ETM3EDLygjN0czW}
```

### New Learnings
1. *cut -d arg1 -f arg2 file_name* command is used to extract particular columns of data from the specified file. The '-d' option specifies how columns are separated in its aregument while the '-f' option takes the column number to be extracted as its argument.
2. Using piping along with *cut* and *tr* commands, we can make entire columns into a single line output.