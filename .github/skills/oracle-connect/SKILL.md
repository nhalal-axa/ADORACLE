---
name: oracle-connect
description: À utiliser pour se connecter dynamiquement à une base Oracle avec les paramètres fournis au moment de la demande, notamment le serveur, le port, le service name, le login et le mot de passe.
license: MIT
---

# Connexion Oracle dynamique

Ce skill établit une connexion Oracle à partir de paramètres fournis au moment de l'utilisation. Il ne contient aucune valeur de connexion permanente.

## Déclenchement

Utiliser ce skill lorsqu'une demande contient une intention telle que :

- « Connecte-toi à la base X » ;
- « Ouvre une connexion Oracle » ;
- « Connecte-toi au serveur Y puis analyse cette erreur ».

## Paramètres obligatoires

Demander uniquement les paramètres manquants :

- `server` : nom DNS ou adresse IP du serveur Oracle ;
- `port` : port du listener Oracle, généralement `1521` ;
- `service_name` : nom du service Oracle ;
- `username` : nom du compte Oracle ;
- `password` : mot de passe fourni de manière sécurisée au moment de la connexion.

Paramètres facultatifs à demander seulement s'ils sont nécessaires :

- protocole ou mode TLS ;
- wallet Oracle ou chemin de certificats ;
- nom de connexion à utiliser dans l'extension ;
- délai d'expiration ;
- rôle Oracle, par exemple `SYSDBA`, uniquement si l'utilisateur le demande explicitement.

## Règles de sécurité

- Ne jamais enregistrer le mot de passe dans ce fichier, dans le dépôt, dans un script ou dans un journal.
- Ne jamais afficher le mot de passe dans une réponse, une commande, une URL ou une chaîne de connexion visible.
- Ne jamais déduire ou inventer une valeur manquante.
- Demander le mot de passe séparément des autres paramètres et utiliser une saisie sécurisée si l'outil le permet.
- Ne pas conserver les identifiants après la fin de la session.
- Refuser de poursuivre si le mot de passe est fourni dans un fichier du dépôt ou dans un contexte manifestement non sécurisé.

## Procédure de connexion

1. Identifier la base cible et recueillir les paramètres obligatoires manquants.
2. Confirmer la cible sous la forme `server:port/service_name`, sans afficher le mot de passe.
3. Utiliser l'extension VS Code « Connect to Server » si elle est installée et expose une action de connexion Oracle.
4. Si l'extension n'est pas disponible, indiquer clairement que le skill ne peut pas ouvrir la connexion seul et demander à l'utilisateur d'ouvrir la connexion avec un outil Oracle disponible.
5. Effectuer uniquement le test de connexion nécessaire, sans exécuter de requête métier ni modifier de données.
6. Confirmer uniquement le résultat de la connexion et le nom de la base ou du service, sans révéler d'identifiant sensible.

## Transmission au dépannage

Si l'utilisateur demande ensuite une analyse :

- transmettre le contexte de connexion au skill `troubleshooting` sans transmettre le mot de passe ;
- conserver le mode consultatif du skill `troubleshooting` ;
- ne pas modifier de données, de schéma, de configuration ou d'objets Oracle ;
- proposer les requêtes ou vérifications nécessaires sans les exécuter automatiquement.

## Exemple de demande

« Connecte-toi à la base `FINANCE` avec le serveur `oracle-prod`, le port `1521` et le service name `FINPRD`. Demande-moi les informations manquantes, puis utilise le skill troubleshooting pour analyser l'erreur ORA-xxxx sans modifier la base. »

## Format de réponse

Avant la connexion, fournir :

1. Les paramètres connus, en masquant toute information sensible.
2. Les paramètres manquants à fournir.
3. La méthode de connexion utilisée.

Après la tentative, fournir :

1. Le résultat de la connexion.
2. Une description non sensible de l'erreur éventuelle.
3. Les prochaines vérifications proposées, sans les exécuter.
