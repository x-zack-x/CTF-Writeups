# Hidden in plainsight

## Category: 
Forensics

## Difficulty
easy

## Description
You’re given a seemingly ordinary JPG image. Something is tucked away out of sight inside the file. Your task is to discover the hidden payload and extract the flag.
Download the jpg image here.
##My approach

##step 1-First observation
The challenge title "Hidden in Plain Sight" combined with 
a JPG file strongly suggested steganography — data hidden 
inside an image without changing its appearance.

##step 2 -What i tried
>"file" i used it to see the image information.
![file cmd](image2.jpeg)
>"cyberchef"(web version)i used it to decode the unreadable phase found in the comment field using the previous command which was a base64 encoding due to the structure of the phase which was letters,numbers,and ended with '='.
![cyberchef output](image3-1.jpeg)
![cyberchef output](image3-2.jpeg)
>"steghide" used it to extract the hidden content 
from the image — the decoded CyberChef output revealed 
"steghide:[password]" which directly indicated steghide 
was the tool needed and provided the passphrase.
![steghide cmd](image4.jpeg)
>"cat" used it to to print the output of the file extracted.
![cat cmd](image5.jpeg)

##step 3 -the solution
After decoding the unreadable comment found in the file output using cyberchef ,we found the word steghide:[password] which was the clue to our hidden flag.The flag was found after extracting it into a file using steghide a tool for embeding and extracting data .

## Flag
picoCTF{h1dd3n_1n_1m4g3_5d4cba73}

## What I learned
Steganography is the process of hiding data inside an image 
without changing its visible appearance — achieved by modifying 
the least significant bits of the file. Steghide is a tool 
specifically used to embed and extract hidden data from images.
