
# Task
####  Vimjail2
Well, the first one was too easy... The vimrc is the same as the previous, we just added one single tiny line. We won't disclose what we added as it would spoil the first one, but you will realize what is blocked pretty quickly...

`ssh user@chall.polygl0ts.ch -p 9024 (password: lakectf)`

# Writeup

We notice after Ssh-ing into the challenge that the technique we used to get the previous solution, "Ctrl+R", is now remapped to "nope". Hence the "one single tiny line" in the vimrc.

This won't stop us, however. Our "Ctrl+Q" exploit still works, and we can still bypass the "_" remapping to all other characters. The only issue now is to execute another system call. This can be done with "Ctrl+X", vim's completion options. 

![](https://imgur.com/3sY74RW.jpg)

All we have to do is hit "Ctrl+X", and then "Ctrl+R=". 

"Ctrl+X" allows us to run "Ctrl+R=", and then we repeat the solution to the previous challenge. That is - we run a system command to find the contents of the flag file.

![](https://imgur.com/gIlDv3C.jpg)

![](https://imgur.com/w4fjcAj.jpg)

The flag is:

EPFL{vim_worse_than_macs_eh}
