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
## Challenge Mod 1  
Reading the problem statement and its requirements, i had no clue what to do so i referred a writeup  
Created a python script for the required conditions:  
```
def decode(number):
    r = number % 37
    return r

def main():
    f = open("message.txt", "r", encoding="UTF-8")
    lst = f.read().split()
    # print(lst[0])

    dec_lst = []

    for i in range(len(lst)):
        dec_lst.append(decode(int(lst[i])))

    print(dec_lst)

if __name__ == '__main__':
    main()
```
As per the condition,  
```
A: 0
B: 1
C: 2
D: 3
E: 4
F: 5
G: 6
H: 7
I: 8
J: 9
K: 10
L: 11
M: 12
N: 13
O: 14
P: 15
Q: 16
R: 17
S: 18
T: 19
U: 20
V: 21
W: 22
X: 23
Y: 24
Z: 25
0: 26
1: 27
2: 28
3: 29
4: 30
5: 31
6: 32
7: 33
8: 34
9: 35
_: 36
```
So the output of the python script i.e. 17, 26, 20, 13, 3, 36, 13, 36, 17, 26, 20, 13, 3, 36, 1, 32, 1, 28, 31, 31, 29, 27 becomes  
R, 0, U, N, D, _, N, _, R, 0, U, N, D, _, B, 6, B, 2, 5, 5, 3, 1 which gives the flag.  
Flag: picoCTF{R0UND_N_R0UND_B6B25531}
