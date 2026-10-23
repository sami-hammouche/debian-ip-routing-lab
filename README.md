# Réseaux et systèmes — projets de L3

Les projets réseau et système de ma licence 3 informatique, parcours Systèmes et Réseaux, à l'Université Évry Paris-Saclay. Chaque dossier contient le rapport complet, avec les commandes, les captures et les analyses.

## Les projets

### [Projet 1 — Routage IP sous Debian](projet-1-routage-ip/)

Trois machines Debian réparties sur deux réseaux, dont une configurée en routeur. Configuration statique des interfaces, activation d'`ip_forward`, puis analyse des trames avec Wireshark pour suivre un paquet de bout en bout : les décisions de routage à chaque étape, la décrémentation du TTL, et le changement des adresses MAC d'un réseau à l'autre alors que les adresses IP restent intactes. Le trajet est étudié à l'aller, au retour, et pour une connexion SSH.

### [Projet 2 — Authentification forte](projet-2-authentification-forte/)

Mise en place d'une authentification à deux facteurs sur SSH entre deux stations Debian : TOTP avec Google Authenticator, configuration de PAM, comparaison de quatre méthodes d'authentification face à un keylogger, et usage d'un gestionnaire de mots de passe.

## Le contexte

Ces rapports sont des travaux universitaires rendus et notés. Ils sont écrits pour expliquer ce qui a été fait et pourquoi, pas seulement pour montrer des commandes qui fonctionnent.
