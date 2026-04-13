# Ph4nt0m 1ntrud3r

## Category: 
Forensics

## Difficulty
Easy

## Description
A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag.
To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder!
Find the PCAP file here [Network Traffic PCAP] file and try to get the flag.

## My approach

## step 1 - First observation

![syn](screenshots/1.jpeg)

il convient de noter que l'analyse du traffic réseau peut être fait par plusieurs outils notamment wireshark.j'ai utilisé ce dernier pour analyser le fichier donné.le traffic ne contenait que des paquets de tcp SYN ce qui était incommun.

## step 2 - What i tried

![syn](screenshots/2.jpeg)



>"filter=tcp.stream eq 0" ce filter a engendré un classement des paquets selon le critère chronologique,nonobstant ce classement peut être incohérent si le timestamp champ est saboté par l'attaqueur.

![syn](screenshots/4.jpeg)


>"cyberchef" l'attaquant a utilisé une methode en matière de stegnographie réseau de sorte que les données exfiltrées soient encodé et invisible pour le firewall. cyberchef m'a aidé ici après une operation d'extraction pour décoder l'extraction base64 ce qui rends la lecture des données extractées intuitive.

## step 3 - The solution

![syn](screenshots/3.jpeg)


la sténographie est un art de commande et contrôle sans compter l'exfiltration et collection. cet art peut être difficile à détecter selon la complexité utilisée par l'attaqueur.dès-lors,j'ai manuellement vérifié chaque champ dans tout les paquets pour déterminer l'anomalie dans ces paquets ,de ce fait j'ai trouvé deux anomalie le nombre de séquence était toujours zero ce qui est inhabituel ainsi que la payload du tcp porté 8/4/16 bytes de données codées en base64.par ailleurs ,après l'assemblage manuelle et le décodage de ces payloads le résultat montre le flag autour de codes incompréhensibles ce qui montre que la pluspart des paquets tcp étaient placés pour le camouflage du flag pour rendre l'analyse plus difficile.

## Flag

picoCTF{it_w4snt_th4t_34sy_tbh_4r_f318db22}

## What I learned

- j'ai appris que la stégnographie est la meilleur méthode pour la technique c2 commande contrôle ou l'exfiltration de données de petites tailles comme les mots de passe sans compter son potentiel à éviter la détection.
- l'utilisation d'un firewall simple n'est pas une option sécurisée ,néanmoins la NGFW (new generation firewall) peuvent lutter contre des méthodes simples de stégnographie sans oublier d'implémenter un analyse profond des paquets et utilisés des algorithmes de surveilles de SEQ Numbers pour éviter pour éviter le sabotage de ce champs …
