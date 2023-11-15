## Challenge: keygenme-py  
Logged into webshell and downloaded the python script. Then executed it via python3 command to see the calculator interface. b is locked and a requires me to mention a star system. c seems to be where i enter the keyphrase.  
Used nano command to look at the code.  
From the code i noticed the key structure:  
![image](https://github.com/Azure9733/picoCTF/assets/143328010/c02b19f8-b6f4-4072-9aa2-a13c96131972)  
I also got the list of star systems which i will use in the calculator now.  
I used different star names but only got the estimated mana burn not anything that looked like akey.  
I couldnt understand the code completely so i referred 'https://github.com/vivian-dai/PicoCTF2021-Writeup/blob/main/Reverse%20Engineering/keygenme-py/keygenme-py.md'.  
I understood that the key must be entered in the license area which will unlock b option.  
And also that the key is of the same length as that of the ctf flag given above in the structure.  
Because of the writeup above i was able to understand that the first half of the static key is part of the key, i.e. "picoCTF{1n_7h3_|<3y_of_"  
The remaining unknown values are equal to the number of if statements. If x is replaced in the provided order of 45362718 i complete the key.  
The next step is heavily influenced by the writeup and it took me a while to understand it.  
What has been done is that parts of the code is taken to another python file which includes the required library i.e. hashlib, the given trial username which in my case is "SCHOFIELD" along with the structure of full key template as well as the 8 if statements with the given x values in sequence:  
```
import hashlib  
username_trial = "SCHOFIELD"  
bUsername_trial = b"SCHOFIELD"  

key_part_static1_trial = "picoCTF{1n_7h3_|<3y_of_"  
key_part_dynamic1_trial = "xxxxxxxx"  
key_part_static2_trial = "}"  
key_full_template_trial = key_part_static1_trial + key_part_dynamic1_trial + key_part_static2_trial  

print(hashlib.sha256(bUsername_trial).hexdigest()[4])  
print(hashlib.sha256(bUsername_trial).hexdigest()[5])  
print(hashlib.sha256(bUsername_trial).hexdigest()[3])  
print(hashlib.sha256(bUsername_trial).hexdigest()[6])  
print(hashlib.sha256(bUsername_trial).hexdigest()[2])  
print(hashlib.sha256(bUsername_trial).hexdigest()[7])  
print(hashlib.sha256(bUsername_trial).hexdigest()[1])  
print(hashlib.sha256(bUsername_trial).hexdigest()[8])
```
This gave the result "e584b363"  
So the flag is "picoCTF{1n_7h3_|<3y_of_e584b363}"
