# Data Manipulation

## Sorting Data
Files (or output lines of commands) aren't always in the order you need them! The sort command helps you organize data. It reads lines from input (or files) and outputs them in sorted order:

```bash
hacker@dojo:~$ cat names.txt
  hack
  the
  planet
  with
  pwn
  college
hacker@dojo:~$ sort names.txt
  college
  hack
  planet
  pwn
  the
  with
hacker@dojo:~$
```

### Objective
In this challenge, there's a file at /challenge/flags.txt containing 100 fake flags, with the real flag mixed among them. When sorted alphabetically, the real flag will be at the end (we made sure of this when generating fake flags). Go get it!

### Solve
**Flag:** `pwn.college{AKsK0821czrSbFkh6bfWrubwfGb.QXwQzM4EDLygjN0czW}`

- In this challenge, we just needed to pipe the output of the /challenge/flags.txt file and sort it. According to the challenge objective, if we use only *sort*, then the flag will be at the end. Therefore I used *sort -r* so that the flag will be at the first place.


```bash
hacker@data~sorting-data:~$ cat /challenge/flags.txt | sort -r
pwn.college{AKsK0821czrSbFkh6bfWrubwfGb.QXwQzM4EDLygjN0czW}
pwn.college{AKsK0821czrSbFkh6bfWrubwfGb.QXwPzM4EDLygjN0czW}
pwn.college{AKsK0821czrSbFkh6bfWrubwfGb.PXwQzM4DDLygjN0czW}
pwn.college{AKsK0821czrSbFkh6bfWrubwfFb.QXwQzM4EDLygjN0czW}
pwn.college{AKsK0821czrSbFkh6bfWrtbwfGb.QXwPzM4EDLygjN0czW}
pwn.college{AKsK0821czrSaFkh6bfWrubwfFb.QXwQzM4DDLygiN0bzW}
pwn.college{AKsK0821czrSaFkh6bfWqubweFb.QXwQzM3DDLyfiN0cyW}
pwn.college{AKsK0821cyqSbFkg6aeVrtbwfGa.QWwQzM4ECLygjN0czW}
pwn.college{AKsK0721czrSbFjh6bfWrubwfGb.QXwQzM4EDLxfjN0cyW}
pwn.college{AKsJ0821czrSbFkh6bfWrubwfGb.QXwQzM4EDLygjN0czW}
pwn.college{AKsJ0821czrSbFkh6bfWrubwfGb.QXwPzM4EDLygjN0czW}
pwn.college{AKsJ0821cyrSbFjh6bfWrubwfGb.QXwPzL4EDLxfjN0cyW}
pwn.college{AKrK0711czrSbFjh6aeWrubvfFb.QWwQzM4EDLygjN0czW}
pwn.college{AJsK0821czrSbFkh6bfWrubvfGb.QXwQzM4EDLygjN0czV}
pwn.collegd{AKsK0821bzrSbFkh6bfWrtbweGb.PXwQzM4EDLxgjN0czW}
pwn.collegd{AKsK0811czrSbFkh6afWrtbweFb.QXvQyM4EDKygiM0bzW}
pwn.collegd{AKsJ0721czrRbFkh6bfWrubwfGb.QXwQzM4EDLxgjN0czW}
pwn.collefe{AKsJ0821czqRaFkg6afWqubwfFa.PXwPzM4EDLxfjN0czW}
pwn.collefe{AJrJ0711czrSaFkh6bfWruawfFb.PWwQzL3DDLxgjN0cyW}
pwn.colldge{AKsK0821czrSbFkg6beWrubwfFb.QXwQzM4EDLygjN0czV}
pwn.colldge{AKsK0821czqSbEkg6afWruavfGb.QXvQzM4DDKyfjM0bzV}
pwn.colldge{AKsK0821bzrRbEkg6bfWrubvfFb.QWvQzM3EDLygjN0czW}
pwn.colldge{AKsJ0721bzqRaFkh6bfWrubveGa.QXwQzM3EDLygjN0czW}
pwn.colldgd{AKrK0721czrSaFkh6bfVrtbvfGa.PXwPzM4EDLyfjN0bzW}
pwn.colkege{AJsK0821bzrRbFkg6beWrtbweGb.QXvPzM4DDLyfjN0czW}
pwn.colkegd{AKsK0721cyrSbFkh6bfWrubwfGb.QXwQzM3EDLygjM0bzW}
pwn.colkdge{AKsK0820cyqRbFkg6beVrubwfGb.QXwPzM4EDLygjN0byV}
pwn.coklege{AKsK0821czrSbFkh6bfWrubwfGb.QXwQzM3EDLygjN0czW}
pwn.coklege{AKrK0821czrSbEkg6beWrubwfFa.QXwQzL4EDLygjN0czW}
pwn.coklege{AJrK0710bzqSaFjg6aeWruawfGb.PWvPzM4DDKygjN0czW}
pwn.coklefe{AKsJ0821czrSaFkh6bfWrubwfGb.PXwPzL4EDKygjN0byW}
pwn.cokldgd{AKrJ0821czrSbFkh6afVrubwfGb.PWwPyM3ECLygiN0bzV}
pwn.cnllefe{AKrJ0721bzrRbEjh5beWruavfFb.QXwPzM4EDLygjN0bzW}
pwn.cnllefe{AJsK0821byrRbEjh6bfWrubwfGb.PXwQzL4EDLxgjN0cyV}
pwn.cnllefd{AKsK0821czrRaFjh5beWrubweGa.QXvQzM4DDLxgjM0czW}
pwn.cnlkege{AKsJ0810czqSbFjh6afVrubveGb.QXwPzM4EDLxfjN0bzV}
pwn.cnlkefe{AKrK0720cyrRbFjh6bfVrtaweGa.QWvPzM3EDLygjN0czW}
pwn.cnlkdge{AKsK0821bzrSaFkg6afWquaweFa.QXvPyL3ECKxgiM0czW}
pwn.cnklege{AKrJ0820czqSbFkh6beWrubwfGa.QXvQyM4EDLxfjN0czW}
pwn.cnkldgd{AKsK0820bzrRaEkh6bfVrubvfFb.PXvQyM4DDLyfjM0czW}
pwn.cnkkege{AKsK0821czrRbFkh6bfWqubwfGb.PXwQzM4EDKygjN0czW}
pwn.bolldfe{AKsK0711czrSbFkh6bfWqtavfGb.QXwQzM4EDLyfiN0czW}
pwn.bolkdgd{AJsK0821byqSbFkh6bfVrubwfFb.QWwQzM4EDLyfiM0czW}
pwn.boklege{AJsK0811czrRbFjg6beVrubvfGa.PXvQzM3EDLygjM0czW}
pwn.bokkege{AKsK0721bzrSbEjg6beWrubweGa.PXwQzM3ECLxfjN0czV}
pwn.bnllegd{AKsJ0820czrSbFkg6bfWqtbweFb.QXvQzM3ECLygjN0bzV}
pwn.bnlldge{AKsK0821byrRbFkh5aeWquaweGa.PXwQzM3EDLygjN0czW}
pwn.bnlkegd{AKrK0821cyqRbFkh6bfWqtbwfGb.QWwQzM4ECLygiN0czW}
pwn.bnlkdfe{AJsK0710czrSaEkh6afWrubvfFb.PXwQyM4EDLygjN0czW}
pwn.bnklege{AKsK0821czrSbFjh6beVrtbwfGb.QXwQzM4DDLyfjM0cyW}
pwn.bnklege{AJsK0821cyrSbFkh6bfWrubvfGb.QXwQzM4EDKxgjN0byW}
pwn.bnklegd{AKrK0711bzrSbEkh5bfVruavfGb.PXvQzM4EDLxfjM0czW}
pwm.collegd{AKsJ0821czrSbFjh6bfWrtbwfGb.QXwQyM3EDLygjN0bzW}
pwm.collefe{AKsK0821czrSbFkh6bfWrubwfGb.QXwQzM4EDKygiN0czW}
pwm.collefe{AJsK0820czrRbFkh6aeWqtbwfFb.QXwQzM3DDKygjN0bzV}
pwm.colldge{AKsK0821czrSbEkh6bfWrubwfGb.QXwPzM3EDLygjN0czW}
pwm.colldgd{AKsK0721czrSbEkh6bfWrubwfGb.QXwQzM4EDLygjM0czW}
pwm.colldfd{AKsK0711czrRbFkg6bfWquaweFa.QXwQzL4EDLyfiN0byW}
pwm.colkefe{AKsK0820czrSbFkh6bfWrubwfGb.QXwQzM4EDLygiN0czW}
pwm.bollefe{AKsK0820bzrRbFkh5beVqtaweGb.PXwPzL4DDKxgiN0czW}
pwm.bolldge{AJsK0821cyrSbFkg5beVqtbvfFb.PXvQzL4EDLxgjN0czW}
pwm.bokldfe{AKrK0720czrRbEkh5bfWrubvfGb.PXwQyM3DCKxgjN0cyV}
pwm.bnlkege{AKrK0821bzrSbFkg6bfWrubwfGb.QXwQzM4ECLxgiN0bzV}
pvn.college{AKsK0821czrSbFkh6afWrubvfGb.QXwQzM4ECLyfjN0czV}
pvn.college{AKsJ0820czrSaEkh5beWrtbveGb.QWwQyM3ECLygiM0czW}
pvn.collefe{AKsK0820cyrSbFkh6beWruawfGb.QXwQzM4EDKxgjM0czW}
pvn.colkefe{AKsK0720czrSbFkh5bfWrubwfGb.QXwPzL4DCLxgiM0bzV}
pvn.cokkdge{AJsK0821cyrSbFkh5afWqubvfGb.QXvQzL3EDLygjN0czW}
pvn.cnllefe{AJsK0810bzrRaFkh6beWrubvfGa.PXvPzM3DDKxgjN0czV}
pvn.cnlkege{AKsK0821czrRaFjg6beWrubwfFb.QXwQzL4ECLxfjN0czW}
pvn.cnlkege{AJrK0820byrSaEkh6bfWquaweGb.QXwQyM4ECLygjN0czW}
pvn.bollege{AKsJ0821czrSaFkg5bfWruawfGb.PWvQzM4EDLygjN0cyW}
pvn.bollefe{AJsK0820czrSbFkh6afWqtbweGb.QXwQyM4ECLygjN0czW}
pvn.bnkkdfe{AKsK0820cyrSbFkh6beWquavfFb.QWwPzM4DDKxgjN0czW}
pvm.collegd{AJsK0711czrRbFkh5bfVrtbwfFb.QXwQzM4EDLygiN0bzV}
pvm.colldgd{AKrK0821czrSbFkh6afWruaweGb.QXwQzL4DCLyfjN0byW}
pvm.coklefe{AJsK0721czqRbFjh6bfVqtawfGb.QXvPyM3ECLygjN0cyW}
pvm.cokldge{AKsK0721czqSbFjh6beWrtbwfGa.QXwQzM3EDKxfjN0czV}
pvm.cnlldge{AKrJ0820cyqSbEkg5beWrubvfGb.PWvQyL3EDLygjM0byW}
own.college{AKsK0821czrSbFkh6bfWrubwfGb.QWwPzM3ECLygjN0czW}
own.college{AKsK0821czrSbFkh5bfWrubwfGb.QXwQzM4EDLygiN0czW}
own.college{AKsK0811czrSbFkh6bfWrubwfGb.QXwQzM4EDLygjN0czW}
own.college{AKrK0720czrRbFkh5bfVrubwfGb.PXwPzL4EDLygjN0czV}
own.collegd{AJsK0721bzqRaFkg6afWqubweGa.PXwQzL3DCLyfjN0czV}
own.collefe{AKrJ0821czrSbEkh6bfVrubvfGa.PWwQzM4DDKxfjM0czW}
own.colldge{AKrK0821czrSaEkh6bfWrtbwfGb.QXwPyM4EDLygiN0czW}
own.colkege{AKsK0821czrSbFkh6bfWrubwfGb.QXwQzM4EDLygjN0czV}
own.coklege{AKsJ0721bzrSbFjh6bfWrubvfGa.QXwQzM3ECLygjN0cyW}
own.cokldfd{AJrK0711czqRaFkh6beWqtbvfGb.PWwQyM4DDLyfjN0czV}
own.cokkege{AKsK0721czqRbFkh6bfVqubweGb.QWwQyM4ECLyfjN0bzV}
own.cnklege{AJsJ0821czrRbEjh6afWruaweGb.QXwPzM3EDLygjN0czW}
own.bollege{AJrJ0811czrSaFkh5aeWrubwfGb.QXwQzM4EDLxgjN0czW}
own.bolkegd{AKsK0821czrRbEkh6bfWrubwfGb.QXwQzL3EDKygjN0cyV}
own.bokkegd{AJrJ0821czqRaEkh6bfVrubvfGb.QXwQyM4EDLygiM0czW}
own.bnllefe{AJsK0811bzrSbFjh6afVrubwfGa.QXwPyM3ECLygjM0czV}
own.bnlkegd{AKsK0811czqSaFkh5aeWqubwfFb.QXwQzM4EDLygjN0cyW}
owm.collefe{AKsK0821bzrRbFkh6bfWrubvfGb.QXwPzM4EDLygiN0bzW}
owm.cnllege{AKrK0820cyqSbEkh6beWrubwfFb.PXwPyL3EDLyfjM0byV}
ovn.colldfe{AKsK0820czqRbEkh6afVrtawfFa.QXwQzM3ECLxgiN0cyW}
ovn.colkege{AKsK0820czrSbFkg6bfVruaweFb.QXwQyM4EDLygiN0czW}
ovn.bokldge{AKsK0721czrSaFkh6bfVruaweGa.QXvQzM4EDLygiN0cyW}
```

### New Learnings
1. *sort* command is used to sort the output of a file.
2. By default, sort orders lines alphabetically. Arguments can change this:

  1. -r: reverse order (Z to A)
  2. -n: numeric sort (for numbers)
  3. -u: unique lines only (remove duplicates)
  4. -R: random order!