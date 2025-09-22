This module will teach the VERY basics of interacting with the command line! The command line lets us execute commands.
When you launch a terminal, it will execute a command line "shell", which will look like this:

```hacker@dojo:~$```

This is called the "prompt", and it's prompting you to enter a command. Let's take a look at what's going on here:

1. The hacker in the prompt is the username of the current user.
2. The @ symbol, or "at" symbol, is a separator. It's used to connect the username to the hostname.
3. The dojo part of the prompt is the hostname of the machine the shell is on.
4. The colon (:) is another separator. It's used to separate the hostname from the current working directory.
5. The tilde (~) is a special symbol that represents the home directory of the current user. 
6. The dollar sign ($) is the prompt symbol. It signifies that the user is a regular, non-privileged user. This is an important distinction. If you were logged in as the root user (the superuser with full administrative privileges), this symbol would typically be a hash (#).