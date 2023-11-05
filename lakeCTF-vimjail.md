# Task

Vimjail: People always koke about how to exit vim. Well, time to show them!

ssh user@chall.polygl0ts.ch -p 9018 (password:lakectf)

# Writeup
Ssh-ing into the challenge leaves us with a vim terminal. 

We immitiately notice that almost every keyboard input is mapped to "_", which is a null character in vimrc

Speaking of vimrc, we're also given a file "chall_vimrc1". It acts as a configuration file for the vimrc, and it just tells us that almost everything in mapped to "_" - both in input and in execution. The lines we care about the most are at the bottom.

![Photo of vimrc](https://i.imgur.com/0wTmUxN.jpg)

These lines mean that "Tab" and "Ctrl+V" are mapped to output "nope" when using in command line mode, and "Ctrl+V" is mapped to output "nope" in input mode.
The rest of the lines map each character input to "_", and map a few more Ctrl keystrokes to "nope". 

This means we can't just copy-paste the lines we want to circumvent the remapping.

First, we need to figure out how to type regular characters. To do that, we use the "Ctrl+Q" command. This allows us to input characters into the vim, bypassing the character remapping. We still need to find a way out of the vim, and simply typing ":q!" using the bypass doesn't get us out yet.

To actually escape the VIM, we need to use "Ctrl+R=". This allows us to run expressions. Expressions *including* system calls.

![](https://imgur.com/JmolFbB.jpg)

Running this command, remembering to hit "Ctrl+Q" before every character typed, gives us:

![](https://imgur.com/yskxhOc.jpg)

We did it! (almost). We have escaped the vim, now we just need to find the contents of the "flag" file. 

![](https://imgur.com/2PD0P3M.jpg)

Running the above system command gets us:

![](https://imgur.com/E4jMdY2.jpg)

The flag is: EPFL{i_could_have_guessed_it}
