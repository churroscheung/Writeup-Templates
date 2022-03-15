# picoGym - flag_shop

* **Category:** General Skills
* **Points:** 300

## Challenge

There's a flag shop selling stuff, can you buy a flag? Source. Connect with nc jupiter.challenges.picoctf.org 44566.

## Solution

According to store.c, the source file given, the system will give us the flag if we purchase a 1337 Flag. However, it costs 100,000, the inital balance is 1100, and there is seemingly no way increase our balance. However, as the amount of knockoff flags desired is an int, it can be overflowed from positive to negative, increasing our balance by having the program subtract a negative number. This can be accomplished by providing it a number, which when multplied by 900, the cost of the knockoff flag, is slightly higher than the maximum value of an integer in C: 2,147,483,647. 

`picoCTF{m0n3y_bag5_68d16363}`




## Thanks to PentaHex CTF for providing the template.
