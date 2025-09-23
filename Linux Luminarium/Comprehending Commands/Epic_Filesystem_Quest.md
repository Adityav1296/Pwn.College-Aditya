# Comprehending Commands 

## Epic Filesystem Quest
With your knowledge of cd, ls, and cat, we're ready to play a little game!

### Objective
In this challenge, I have hidden the flag! Here, you will use ls and cat to follow my breadcrumbs and find it! Here's how it'll work:

1. Your first clue is in /. Head on over there.
2. Look around with ls. There'll be a file named HINT or CLUE or something along those lines!
3. cat that file to read the clue!
4. Depending on what the clue says, head on over to the next directory (or don't!).
5. Follow the clues to the flag!

### Solve
**Flag:** `pwn.college{Mb-ZxWNtXS6_gdmjBHbeby8zM5q.dljM4QDLygjN0czW}`

1. In this challenge, I started in by changing my directory to root(/) as is required. There I ran the *ls* command to list the contents of the directory and found a NOTE file.  
2. Using *cat NOTE*, I found the next clue but the clue itself was trapped and I needed to read it without 'cd'ing into the next directory I found.  
3. Therefore, I used *ls -a* command with argument as the new directory `/usr/lib/python3/dist-packages/sympy/printing/pretty/tests/__pycache__` to list out all the files present inside the new directory.  
4. There I found the SPOILER-TRAPPED file. Using *cat* command with `/usr/lib/python3/dist-packages/sympy/printing/pretty/tests/__pycache__/SPOILER-TRAPPED` as the argument, I found the next clue which was a new directory.  
5. Again I repeated the step 3 with the new directory `/usr/lib/python3/dist-packages/networkx/algorithms/bipartite` as argument and found LEAD file in it. Applying step 4 with `/usr/lib/python3/dist-packages/networkx/algorithms/bipartite/LEAD` as argument I got to the next clue which was a new directory again. This clue can only be opened after changing the directory to the new one.  
6. So I used `cd /usr/share/icons/ubuntu-mono-light/actions/16` to get to the new directory and then ran the *ls -a* command to list out the files. There I found the ALERT file. Using `cat ALERT` I read its content. This time I got a new directory and hint that the next clue is a hidden file.  
7. Again I used `cd /opt/linux/linux-5.4/drivers/staging/most/Documentation` to get to the new directory and then ran the *ls -a* command to list out the files. There I found the .BRIEF file. Using `cat BRIEF` I read its content. This time I got a new directory and a trapped clue.  
8. I ran `ls -a /usr/local/lib/python3.8/dist-packages/babel/messages/__pycache__` to list the files in the new directory and this time I found DISPATCH-TRAPPED file. Using `cat /usr/local/lib/python3.8/dist-packages/babel/messages/__pycache__/DISPATCH-TRAPPED`, I read its content. The next clue was a delayed clue that can only be opened after changing the directory to the new one.  
9. Using `cd /usr/share/maxima-sage/5.42.2/share/pdiff` I went to the new directory and used *ls -a* to list out the files in it. There I found the INFO file and on using `cat INFO`, it displayed the new directory to go to and that the next clue is a hidden clue.  
10. Using `cd /usr/lib/python3/dist-packages/sage/modules/__pycache__` I went to the new directory and used *ls -a* to list out the files in it. There I found the .TEASER file and on using `cat .TEASER`, the next clue was a new directory with a hidden clue file in it.  
11. This time, I directly listed the contents of the new directory using `ls -a /opt/linux/linux-5.4/include/config/pcmcia` and found the .SECRET file. Then I used `cat .SECRET` and finally obtained the required flag.

```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
NOTE  challenge  flag  lib32   media  opt   run   sys  var
bin   dev        home  lib64   mnt    proc  sbin  tmp
boot  etc        lib   libx32  nix    root  srv   usr
hacker@commands~an-epic-filesystem-quest:/$ cat NOTE
Tubular find!
The next clue is in: /usr/lib/python3/dist-packages/sympy/printing/pretty/tests/__pycache__

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/$ ls -a /usr/lib/python3/dist-packages/sympy/printing/pretty/tests/__pycache__
.  ..  SPOILER-TRAPPED  __init__.cpython-38.pyc  test_pretty.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/$ cat /usr/lib/python3/dist-packages/sympy/printing/pretty/tests/__pycache__/SPOILER-TRAPPED
Tubular find!
The next clue is in: /usr/lib/python3/dist-packages/networkx/algorithms/bipartite

hacker@commands~an-epic-filesystem-quest:/$ ls -a /usr/lib/python3/dist-packages/networkx/algorithms/bipartite
.     __init__.py  centrality.py  edgelist.py    matrix.py      spectral.py
..    __pycache__  cluster.py     generators.py  projection.py  tests
LEAD  basic.py     covering.py    matching.py    redundancy.py
hacker@commands~an-epic-filesystem-quest:/$ cat /usr/lib/python3/dist-packages/networkx/algorithms/bipartite/LEAD
Tubular find!
The next clue is in: /usr/share/icons/ubuntu-mono-light/actions/16

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/share/icons/ubuntu-mono-light/actions/16
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/ubuntu-mono-light/actions/16$ ls -a
.                                  system-shutdown-panel.svg
..                                 window-close-symbolic.svg
ALERT                              window-maximize-symbolic.svg
package-supported.svg              window-minimize-symbolic.svg
system-restart-panel.svg           window-restore-symbolic.svg
system-shutdown-panel-restart.svg
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/ubuntu-mono-light/actions/16$ cat ./ALERT
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/drivers/staging/most/Documentation

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:~$ cd  /opt/linux/linux-5.4/drivers/staging/most/Documentation
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/most/Documentation$ ls -a
.  ..  .BRIEF  ABI  driver_usage.txt
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/most/Documentation$ cat .BRIEF
Great sleuthing!
The next clue is in: /usr/local/lib/python3.8/dist-packages/babel/messages/__pycache__

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/most/Documentation$ ls -a /usr/local/lib/python3.8/dist-packages/babel/messages/__pycache__
.                        extract.cpython-38.pyc
..                       frontend.cpython-38.pyc
DISPATCH-TRAPPED         jslexer.cpython-38.pyc
__init__.cpython-38.pyc  mofile.cpython-38.pyc
_compat.cpython-38.pyc   plurals.cpython-38.pyc
catalog.cpython-38.pyc   pofile.cpython-38.pyc
checkers.cpython-38.pyc  setuptools_frontend.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/most/Documentation$ cat /usr/local/lib/python3.8/dist-packages/babel/messages/__pycache__/DISPATCH-TRAPPED
Yahaha, you found me!
The next clue is in: /usr/share/maxima-sage/5.42.2/share/pdiff

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/most/Documentation$ cd /usr/share/maxima-sage/5.42.2/share/pdiff
hacker@commands~an-epic-filesystem-quest:/usr/share/maxima-sage/5.42.2/share/pdiff$ ls
INFO        history.txt    pdiff-doc.tex  rtest_pdiff.mac
battex.sty  pdiff-doc.pdf  pdiff.lisp
hacker@commands~an-epic-filesystem-quest:/usr/share/maxima-sage/5.42.2/share/pdiff$ cat INFO
Great sleuthing!
The next clue is in: /usr/lib/python3/dist-packages/sage/modules/__pycache__

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/share/maxima-sage/5.42.2/share/pdiff$ cd /usr/lib/python3/dist-packages/sage/modules/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/modules/__pycache__$ ls -a
.
..
.TEASER
__init__.cpython-38.pyc
all.cpython-38.pyc
complex_double_vector.cpython-38.pyc
diamond_cutting.cpython-38.pyc
filtered_vector_space.cpython-38.pyc
free_module.cpython-38.pyc
free_module_homspace.cpython-38.pyc
free_module_integer.cpython-38.pyc
free_module_morphism.cpython-38.pyc
free_quadratic_module.cpython-38.pyc
free_quadratic_module_integer_symmetric.cpython-38.pyc
matrix_morphism.cpython-38.pyc
misc.cpython-38.pyc
module_functors.cpython-38.pyc
multi_filtered_vector_space.cpython-38.pyc
quotient_module.cpython-38.pyc
real_double_vector.cpython-38.pyc
tensor_operations.cpython-38.pyc
torsion_quadratic_module.cpython-38.pyc
tutorial_free_modules.cpython-38.pyc
vector_callable_symbolic_dense.cpython-38.pyc
vector_space_homspace.cpython-38.pyc
vector_space_morphism.cpython-38.pyc
vector_symbolic_dense.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/modules/__pycache__$ cat .TEASER
Congratulations, you found the clue!
The next clue is in: /opt/linux/linux-5.4/include/config/pcmcia

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/modules/__pycache__$ ls -a /opt/linux/linux-5.4/include/config/pcmcia
.  ..  .SECRET  load
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/modules/__pycache__$ cat /opt/linux/linux-5.4/include/config/pcmcia/.SECRET
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{Mb-ZxWNtXS6_gdmjBHbeby8zM5q.dljM4QDLygjN0czW}
```

### New Learning
1. Applying multiple commands one after another.  
2. Accessing the contents of a different directory by using the *ls* and *cat* commands while staying in the current directory.
