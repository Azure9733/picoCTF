## Challenge: New Ceaser.py  
Looking at the code, the key can only be of 1 character and the string can have upto 16 lowercase ascii characters.  
did not know what to do next so i referred a writeup 'https://ctftime.org/writeup/28927'.  
running the file gave assertion error.  
I followed the steps in the writeup.  
Changed the shift function to subtract
used the python script (while understanding it)  
```
# import string
import string

# constants
LOWERCASE_OFFSET = ord("a")
ALPHABET = string.ascii_lowercase[:16]

# decode function
def b16_decode(cipher):
    dec = ""
    # loop through the cipher 2 characters at a time
    for c in range(0, len(cipher), 2):
        # turn the two characters into one binary string
        b = ""
        b += "{0:b}".format(ALPHABET.index(cipher[c])).zfill(4)
        b += "{0:b}".format(ALPHABET.index(cipher[c+1])).zfill(4)
        # turn the binary string to a character and add
        dec += chr(int(b,2))
    
    # return
    return dec

# unshift the text
def unshift(c, k):
    t1 = ord(c) - LOWERCASE_OFFSET
    t2 = ord(k) - LOWERCASE_OFFSET
    return ALPHABET[(t1 - t2) % len(ALPHABET)]

# encrypted flag
enc = "ihjghbjgjhfbhbfcfjflfjiifdfgffihfeigidfligigffihfjfhfhfhigfjfffjfeihihfdieieih"

# loop through all possible keys
for key in ALPHABET:
    # initialize string
    s = ""

    # loop through the encrypted text
    for i,c in enumerate(enc):
        # unshift it based on key
        s += unshift(c, key[i % len(key)])

    # decode
    s = b16_decode(s)

    # print key
    print(s)
```
which gives 'et_tu?_0797f143e2da9dd3e7555d7372ee1bbe'  
flag: picoCTF{et_tu?_0797f143e2da9dd3e7555d7372ee1bbe}
