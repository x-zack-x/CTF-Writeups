# Head-Dump

## Category
Web Exploitation

## Difficulty
Easy

## Description
Welcome to the challenge! In this challenge,
you will explore a web application and find
an endpoint that exposes a file containing
a hidden flag.
The application is a simple blog website where
you can read articles about various topics,
including an article about API Documentation.
Your goal is to explore the application and find
the endpoint that generates files holding the
server's memory, where a secret flag is hidden.

## My Approach

## Step 1 — First Observation
Premièrement, j'ai essayé de faire des requêtes
en mode brute-force pour voir s'il existe des
répertoires accessibles sur cette URL.

## Step 2 — What I tried
>> "curl -X GET 'URL'" pour voir la page principale
   du site et accéder aux endpoints trouvés
   par gobuster.
![urlwebpage](images/1.jpeg) 


>> "gobuster dir -u 'URL' -w '/usr/share/seclists/
   Discovery/Web-Content/common.txt'" utilisé pour
   découvrir les différents endpoints accessibles.
![enumeration](images/2.jpeg) 


>> "curl -X GET 'url/heapdump' --output file"
   pour stocker le contenu du heapdump sur notre
   machine locale afin de chercher si un flag
   s'y trouve.
![urlwebpage](images/3.jpeg) 


>> "cat file | grep -o 'picoCTF{.*}'" pour
   rechercher si le flag se trouve dans ce fichier.
![urlwebpage](images/4.jpeg) 


## Step 3 — Solution
J'ai d'abord scanné le site pour trouver les
endpoints accessibles. L'un d'eux était /api-docs,
qui ne devrait pas être accessible en production.
Ce répertoire est destiné aux développeurs et
contient toutes les méthodes et les endpoints
sensibles, dont /heapdump — responsable de
l'allocation mémoire du serveur et c'est là
où le flag se trouvait.

## Flag
picoCTF{Pat!3nt_15_Th3_K3y_dcffa92e}

## What I Learned
>> Bien que gobuster soit le bon outil pour
   l'énumération, ses résultats peuvent être
   inexacts si on n'utilise pas la bonne wordlist.

>> Sur n'importe quel site, avant de le rendre
   public, les développeurs doivent vérifier la
   liste des endpoints disponibles afin de
   supprimer ou restreindre l'accès à certains
   d'entre eux, car la plupart du temps leur rôle
   est d'accélérer les performances ou de partager
   des informations sensibles entre développeurs.

>> Cette vulnérabilité correspond à
   OWASP A05 — Security Misconfiguration :
   un endpoint de debug laissé accessible
   en production.
