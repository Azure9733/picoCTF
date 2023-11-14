## Challenge: tunn3l v1s10n  
Download the given file via webshell.  
Checked its file format -> data  
tried cat and got disconnected from the webshell.  
I tried using different variations of the grep command but nothing worked.  
I looked up a writeup to understand what exactly to do since i could not even think of an approach to begin with.  
I referred 'https://github.com/vivian-dai/PicoCTF2021-Writeup/blob/main/Forensics/tunn3l%20v1s10n/tunn3l%20v1s10n.md'  
Shifted to virtual machine to use hex editors.  
While i was downloading the GNOME Hex Editor, i tried to opent he tunn3lv1s10on file with the default image viewer and got the prompt saying the "bmp image had unsupported header size". This gave me 2 important details.  
1. The file is BMP format.
2. There is something wrong with the header.  
![image](https://github.com/Azure9733/picoCTF/assets/143328010/4ee64442-dcf3-45dd-b6d8-134a57883726)  
I reffered the blog shared in the writeup about BMP format 'https://www.ece.ualberta.ca/~elliott/ee552/studentAppNotes/2003_w/misc/bmp_file_format/bmp_file_format.htm' & 'https://www.ece.ualberta.ca/~elliott/ee552/studentAppNotes/2003_w/misc/bmp_file_format/bmp_file_format.htm'  
Given the clue, i focused on header and infoheader categories.  
I opened the file with photopea.com  
As expected it says not a flag and is oddly stretched out.  
The width of the bitmap is at offset 0x12 and height is at 0x16. I gave height the same values as that of width, i.e. 6E 04 and saved it.  
![Screenshot 2023-11-14 202630](https://github.com/Azure9733/picoCTF/assets/143328010/cea2f81d-6a2d-4fad-8923-6429691baf07)
![Screenshot 2023-11-14 202944](https://github.com/Azure9733/picoCTF/assets/143328010/fab30c07-219f-46f6-a470-43ead9bccd68)  
Opening it on photopea gave me the correct flag.  
![image](https://github.com/Azure9733/picoCTF/assets/143328010/33966840-2ee8-4b2c-9fcf-8ee48c160b7b)  
picoCTF{qu1t3_a_v13w_2020}
