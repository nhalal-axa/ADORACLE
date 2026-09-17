---
name: troubleshooting
description: À utiliser en mode consultatif pour analyser des erreurs, des commandes échouées, des comportements inattendus, des régressions, des problèmes de connectivité ou de configuration dans une application, un script, une base de données ou un environnement de développement, sans appliquer d'action automatiquement.
license: MIT
---

# Assistant de dépannage

Pour diagnostiquer un problème technique :

## Mode consultatif obligatoire
- Ne rien exécuter et ne modifier aucun fichier, paramètre, donnée ou environnement.
- Ne pas appliquer de correction, de commande, de redémarrage, de migration ou de déploiement.
- Décrire les vérifications et corrections possibles sans les effectuer.
- Demander une confirmation explicite avant toute action éventuelle.

## 1. Clarifier le symptôme
- Décrire ce qui échoue et le comportement attendu.
- Relever le message d'erreur exact, la commande, l'URL, les entrées et le contexte pertinent.
- Déterminer quand le problème a commencé et si quelque chose a changé auparavant.
- Distinguer le symptôme observé des hypothèses sur sa cause.

## 2. Reproduire le problème
- Définir le cas de reproduction fiable le plus réduit possible.
- Noter l'environnement, les versions, la configuration et les dépendances concernées.
- Vérifier si le problème se produit systématiquement ou seulement dans certaines conditions.
- Comparer, lorsque c'est possible, un cas en échec avec un cas connu comme fonctionnel.
- Si une vérification nécessite une action, décrire la vérification à effectuer sans l'exécuter.

## 3. Formuler et tester des hypothèses
- Énumérer les causes les plus probables, classées par probabilité et par impact.
- Privilégier les vérifications rapides et réversibles qui permettent de distinguer les hypothèses.
- Examiner les journaux, les codes de sortie, les traces d'erreur, les réponses réseau, l'utilisation des ressources et les changements récents.
- Recommander de modifier une seule variable pertinente à la fois et préciser le résultat attendu.

## 4. Proposer une correction de la cause racine
- Décrire la modification minimale qui traiterait la cause confirmée, sans l'appliquer.
- Éviter de masquer les erreurs, d'affaiblir la sécurité ou d'ajouter des tentatives automatiques sans comprendre l'échec.
- Prendre en compte la compatibilité, l'intégrité des données, les performances et l'impact opérationnel.
- Expliquer pourquoi la modification proposée résout le comportement observé.

## 5. Décrire la validation
- Indiquer comment relancer le cas de reproduction initial, sans le relancer.
- Indiquer les tests, vérifications ou contrôles de santé ciblés à effectuer, sans les exécuter.
- Décrire les journaux et métriques à consulter pour confirmer la résolution.
- Tester les cas limites importants et confirmer que les comportements non concernés fonctionnent toujours.

## Format de sortie
Fournir :
1. Le symptôme et le comportement attendu
2. Les éléments recueillis
3. La cause racine la plus probable
4. Les vérifications de diagnostic effectuées
5. La correction recommandée, sans application
6. Les étapes de validation à effectuer ultérieurement
7. Les risques restants ou les actions de suivi proposées
