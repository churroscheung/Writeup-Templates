# picoGym - Pitter, Patter, Platters

* **Category:** Forensics
* **Points:** 200

## Challenge

'Suspicious' is written all over this disk image. Download suspicious.dd.sda1

## Solution

According to the file command, the file provided is a filesystem, meaning that a disk forensics tool like Autopsy is helpful. Looking at the file in Autopsy, there is a file named suspicious-file.txt, which contains "Nothing to see here! But you may want to look here -->". While this may look like a dead end, the inode may have more information, which can be acquired by looking under the Meta column. Searching this number up in the metadata section of Autopsy, a direct block can be accessed, containing the flag but reversed and with a . between each character. 

`picoCTF{b3_5t111_mL|_<3_ba880921}`





## Thanks to PentaHex CTF for providing the template.
