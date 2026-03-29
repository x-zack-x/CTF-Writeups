# Cookie Monster Secret Recipe

## Category
Web Exploitation

## Difficulty
Easy

## Description
Cookie Monster has hidden his top-secret
cookie recipe somewhere on his website.
As an aspiring cookie detective, your mission
is to uncover this delectable secret.
Can you outsmart Cookie Monster and find
the hidden recipe?

## My Approach
![page](screenshots/1.jpeg)
## Step 1 — First Observation
Ma première approche était de visiter le site.
Par ailleurs, j'ai utilisé Burp Suite pour
analyser les requêtes et les réponses du site
en faisant des tentatives supervisées.

![page](screenshots/2.jpeg)



## Step 2 — What I tried

> Burp Suite / Intercept → Request
  utilisé pour intercepter et interpréter
  les requêtes et les réponses HTTP.
> Burp Suite / Intercept → Inspector
  utilisé pour décoder la valeur
  du cookie trouvée dans la requête.

![page](screenshots/3.jpeg)


## Step 3 — Solution
Après avoir envoyé ma première requête,
j'ai remarqué le header `Cookie` qui
contenait une valeur `secret_recipe`
en format URL encodé. J'ai utilisé
l'onglet Inspector de Burp Suite pour
décoder cette valeur, ce qui a révélé
directement le flag.

## Flag
picoCTF{c00kie_m0nster_l0ves_c00kies_A6FA07D8}

## What I Learned
- Un site web utilise souvent des cookies
  pour maintenir une session active, ce qui
  peut créer des vulnérabilités si les données
  sensibles y sont stockées en clair.

- Chaque site web doit appliquer des
  restrictions au niveau des en-têtes HTTP
  pour éviter toute tentative d'altération
  pouvant compromettre la confidentialité.

- L'utilisation de HTTPS au lieu de HTTP
  est indispensable pour éviter des attaques
  telles que l'homme du milieu (MITM).

- Cette vulnérabilité correspond à
  OWASP A02 — Cryptographic Failures :
  des données sensibles stockées en clair
  dans un cookie sans chiffrement.
