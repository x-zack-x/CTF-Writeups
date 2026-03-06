# RIDDLE REGISTRY

## Category: FORENSICS


## Difficulty
Easy

## Description
Hi, intrepid investigator! 📄🔍 You've stumbled upon a peculiar PDF filled with what seems like nothing more than garbled nonsense. But beware! Not everything is as it appears. Amidst the chaos lies a hidden treasure—an elusive flag waiting to be uncovered.
Find the PDF file here [link] and uncover the flag within the metadata.

## My Approach

##step 1-First observation
First from the description i can understand that the content of the file is useless . I realized that we need to work with the metadata of the file .

##step 2 -What i tried
>"curl" to get the file content via a link.
>"cat" to see the content of the file which was unreadable.
>"pdfinfo" to get the metadata of the file but it was unavailable in the webshell.
>"exiftool"(exchangeable image file format) to see the metadata hidden in the file.
>"cyberchef"(web version)to decode the unreadable phrase in the field author.

##step 3 -the solution
After using exiftool to get the metadata ,i noticed the author field with an unreadable phrase containing letters,numbers and ending with = which was a strong indicator of base64 encoding ,so used cyberchef to decode it and it was the actual flag.

## Flag
picoCTF{puzzl3d_m3tadata_f0und!_ee454950}

## What I learned
Files such as PDFs contain metadata fields (Author, Creator, 
Producer etc.) that are not visible in the normal content. 
Tools like exiftool and pdfinfo can extract this metadata 
which may contain hidden information or encoded flags.
Additionally, Base64 encoded strings can be identified by 
their alphanumeric characters ending with "=".
