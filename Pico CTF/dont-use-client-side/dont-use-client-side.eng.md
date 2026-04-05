# dont-use-client-side

## Category: 
Web Exploitation

## Difficulty
Easy

## Description
Can you break into this super secure portal?
http://fickle-tempest.picoctf.net:51751

## My approach

![accueille](screenshots/1.jpeg)

## step 1 - First observation
First, I used the provided link to access the website. **Furthermore**, I started by inspecting the site.

## step 2 - What i tried
> **"Inspect section/Elements tab"**: Used to analyze the code because the developer might have forgotten one or more sensitive pieces of information capable of being used for site penetration.

![accueille](screenshots/2.jpeg)

## step 3 - The solution

![accueille](screenshots/3.jpeg)

**Consequently**, an authentication code was detected containing a block whose role is to compare the user input with the password by dividing the two components. In terms of security, leaving the verification visible to inspectors is strongly discouraged.

## Flag
picoCTF{no_clients_plz_2eb02b45}

## What I learned
- I learned that verification by **hashing** is the best method for security. It highlights data confidentiality by encrypting information in a database with hash functions characterized by **irreversibility**, ensuring that verification is done without showing sensitive data.
- I also learned how to **"obfuscate"** source code to make it opaque and difficult to read.
- Although this information is not directly applied in this CTF, I believe that input restriction is crucial to avoid **SQL injection** or **Template injection**.
