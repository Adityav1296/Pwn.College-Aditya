# Comprehending Commands 

## Grepping for a Needle in a Haystack
Sometimes, the files that you might cat out are too big. Luckily, we have the grep command to search for the contents we need! There are many ways to grep, and we'll learn one way here:

```
hacker@dojo:~$ grep SEARCH_STRING /path/to/file
```

Invoked like this, grep will search the file for lines of text containing SEARCH_STRING and print them to the console.

### Objective
In this challenge, I've put a hundred thousand lines of text into the /challenge/data.txt file. grep it for the flag!

### Solve
**Flag:** `pwn.college{8VxLjaUtYXxbwLxzM9i3RCzv5n7.ddTM4QDLygjN0czW}`

-> In this challenge, firstly I used the *grep* command with *pwn.college* as the search string as flags here begin with pwn.college and added the absolute path to the target file at the end to get the flag.  
-> Then I also changed my directory to root(/) and checked out the *grep* command there as well with two different paths to the file :  
  - First I used *./data.txt* which is a relative path to the target file.  
  - Second I directly put the file name in place of the path since we were already in the */challenge* directory where the data.txt file can be directly accessed.  

```bash
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{8VxLjaUtYXxbwLxzM9i3RCzv5n7.ddTM4QDLygjN0czW}
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ cd /challenge
hacker@commands~grepping-for-a-needle-in-a-haystack:/challenge$ grep pwn.college ./data.txt
pwn.college{8VxLjaUtYXxbwLxzM9i3RCzv5n7.ddTM4QDLygjN0czW}
hacker@commands~grepping-for-a-needle-in-a-haystack:/challenge$ grep pwn.college data.txt
pwn.college{8VxLjaUtYXxbwLxzM9i3RCzv5n7.ddTM4QDLygjN0czW}
```

### New Learning
1. grep command can be used to find a particule string from a big file and can be useful for looking for the necessary flags or info in big text files.  
2. By default, grep shows all the occurrences of the search string in the target file.  
3. Additional grep commands : 
   1. `grep -n "pwn.college" file.txt` → show line numbers too.  
   2. `grep -c "pwn.college" file.txt` → show count of matching lines.  
   3. `grep -o "pwn.college" file.txt` → print only the matching words, one per occurrence.  

   ```
   hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep -n "pwn.college" /challenge/data.txt
   80270:pwn.college{8VxLjaUtYXxbwLxzM9i3RCzv5n7.ddTM4QDLygjN0czW}
   hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep -o "pwn.college"
   /challenge/data.txt
   pwn.college
   hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep -c "pwn.college"
   /challenge/data.txt
   1
   ```

### References 
1. Chatgpt for additional grep commands.