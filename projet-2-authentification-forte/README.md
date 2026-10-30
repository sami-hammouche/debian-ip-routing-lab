![Capture 1](images/01.png)

# Projet 2 — Authentification forte

## UNIVERSITÉ D'ÉVRY PARIS-SACLAY

Licence 3 : Informatique – SR

RAPPORT DE PROJET

_____________________________________________________________

## AUTHENTIFICATION FORTE

Deuxième projet réseau : TOTP, PAM et gestionnaire de mots de passe.

______________________________________________________________________________

### Réalisé par :

**HAMMOUCHE Sami** – n° étudiant : 20243631

Année universitaire 2026 – 2027

## Maquette :

La maquette est constituée de deux machines virtuelles Debian : station1 (client SSH) et station2 (serveur SSH).
Station1 :
On change le nom de la machine :

![Capture 2](images/02.png)

Puis on modifie /etc/hosts avec vi et on remplace debian par station1.

![Capture 3](images/03.png)

![Capture 4](images/04.png)

## Station2 :

On installe le serveur SSH : On change le nom de la machine :

![Capture 5](images/05.png)

![Capture 6](images/06.png)

Puis on modifie /etc/hosts avec vi et on remplace debian par station2.

![Capture 7](images/07.png)

![Capture 8](images/08.png)

![Capture 9](images/09.png)

première connexion SSH de station1 vers station2

![Capture 10](images/10.png)

connexion SSH réussie avec le mot de passe

## 2. Authentification TOTP avec Google Authenticator

Tutoriel utilisé : https://www.it-connect.fr/linux-comment-activer-le-mfa-sur-un-acces-ssh/

On fera toutes les configurations sur station2, car c’est le serveur SSH qui vérifie le code. Le module PAM **pam_google_authenticator** calcule le code attendu à partir d’un secret partagé avec l’application.

![Capture 11](images/11.png)

Sur station2, on installe le module :
apt install libpam-google-authenticator

Après, on génère le secret pour l’utilisateur debian : on configure le module avec la commande google-authenticator.

![Capture 12](images/12.png)

![Capture 13](images/13.png)

Cela va générer un QR code que l’on va scanner avec notre téléphone.

La commande google-authenticator pose ensuite plusieurs questions :

- Tokens basés sur le temps (yes)
- Mise à jour du fichier ~/.google_authenticator (yes)
- Interdire plusieurs utilisations du même code (yes)
- Augmenter la fenêtre de temps (yes)
- Limitation des tentatives (yes)

Ensuite, on active le MFA sur la connexion SSH en modifiant /etc/pam.d/sshd : on ajoute cette ligne (auth required pam_google_authenticator.so)

![Capture 14](images/14.png)

Après, on configure le serveur SSH : dans /etc/ssh/sshd_config, on met l’option KbdInteractiveAuthentication à yes (sur le site utilisé comme tutoriel, cette option porte un autre nom).

![Capture 15](images/15.png)

Maintenant, quand on est sur station1 et qu’on fait ssh debian@station2, on nous demande en plus le code.

![Capture 16](images/16.png)

*(rapport en cours de rédaction)*
