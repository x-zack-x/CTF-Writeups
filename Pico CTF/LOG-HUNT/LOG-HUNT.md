# LOG HUNT

## Category: General skills


## Difficulty
Easy

## Description
Our server seems to be leaking pieces of a secret flag in its logs. The parts are scattered and sometimes repeated. Can you reconstruct the original flag?
Download the logs and figure out the full flag from the fragments.

## My Approach

## step 1-First observation
First the description scpecified the type of the file which is log so its gonna surely contain timestamps and server's activity. that's why i needed to see it content .


## step 2 -What i tried
>"curl" i used it to get the log via a link.
>"cat"& "head" i used cat to show the content of the log pipped it with head to see only the first 20 line to get an idea of the structure.
>"grep" i used it with cat because i noticed that the flag part have a specific structure "FLAGPART" which is different than the other activities.
>"cut -c" i use cut we the previous command to leave only the interesting field .
"sort -u" is used it to eradicate the duplicates so i can assemble the flag alone.
## step 3 -the solution
After filtering the content of the log and leaving only the flag part we get the flag parts .The only thing left is to bring the piece together so i manually assembled them in order to reconstruct the full flag.

## Flag
picoCTF{us3_y0urlinux_sk1lls_cedfa5fb}

## What I learned
This ctf helped refine my skills in filtering and manipulating content of the file .the main skill was showing specific line using grep , also allowing only specific number of caracter in every line with cut -c and getting ride of duplicates using sort -u. 
