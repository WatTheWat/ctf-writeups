## Task
### Color Me Impressed

 There have been some encrypted documents being passed around on the Ghost Town forum. When asked for the password, someone just posted a link to some web color template tool. We don't know what to make of this. Do you?

Submit the flag as flag{flag_text}.

## Writeup
We find the following posts on the Ghost town forum:

![](https://imgur.com/dY51jVP.png)

The flight_logs.zip file is encrypted with a key. We find the hidden key a few comments later:

![](https://imgur.com/rGp5wrh.png)

This problem is similar to the “internet freedom flag”, in which hex values - represented by each color's hex code - are used as an encryption key.

Using a dropper tool in something like Photoshop (or Photopea), we can find the hex values of each of the colors:

(Left to right)

1.  #476c40
2.  #353548
3.  #237524
4.  #332474
5.  4f6e33
6.  536d40
7.  35680a

Combine all of those values into one string:

 476c403535482375243324744f6e33536d4035680a

Now all we need is  a tool to change the above output from hex.

![](https://imgur.com/MXzcRpg.jpg)


I used Cyberchef (a tool I highly recommend for any cryptography CTF challenge) and the result was:

Gl@55H#u$3$tOn3Sm@5h

We aren't quite done yet. Now we just use the above password to open the zip file. Inside the zip file there are flight logs. All I did was "Ctrl+F" the keyword “flag"

We find the flag on the last line of the file,

flag{D3@dF@c3Rulz!}
