This module will teach you about input and output redirection. Simply put, every process in Linux has three initial, standard channels of communication:

1. Standard Input is the channel through which the process takes input. For example, your shell uses Standard Input to read the commands that you input.
2. Standard Output is the channel through which processes output normal data, such as the flag when it is printed to you in previous challenges or the output of utilities such as ls.
3. Standard Error is the channel through which processes output error details. For example, if you mistype a command, the shell will output, over standard error, that this command does not exist.

Because these three channels are used so frequently in Linux, they are known by shorter names: stdin, stdout, stderr. This module will teach you how to redirect, chain, block, and otherwise mess with these channels.