# Contribuer à UGANC GUIDE

Ce document fixe les règles de travail communes à tous les dépôts de l'organisation **uganc-guide-team**. Il est court : lisez-le en entier avant votre première contribution.

## 1. Le principe : on ne travaille jamais directement sur `main`

La branche `main` contient toujours une version qui fonctionne. Personne ne pousse directement dessus : tout passe par une **branche de travail** puis une **demande de fusion** (pull request) relue par un autre membre.

```
main ──●──────────────●──────────●──
        \            /          /
         feat/12-recherche     fix/18-carte-mobile
```

Ce fonctionnement s'appelle le *GitHub Flow*. Nous n'utilisons pas de branche `develop` : pour une équipe de notre taille, une seule branche principale suffit et évite les confusions.

## 2. Le cycle de travail, étape par étape

1. **Choisir un ticket** (issue) dans le tableau GitHub Projects et s'y assigner. Pas de ticket ? On en crée un d'abord.
2. **Mettre `main` à jour** sur son ordinateur :
   ```bash
   git switch main
   git pull
   ```
3. **Créer une branche** nommée selon la section 3 :
   ```bash
   git switch -c feat/12-barre-de-recherche
   ```
4. **Travailler par petits commits**, nommés selon la section 4.
5. **Pousser la branche** :
   ```bash
   git push -u origin feat/12-barre-de-recherche
   ```
6. **Ouvrir une demande de fusion** vers `main` et remplir le modèle proposé.
7. **Faire relire** : au moins **une approbation** d'un autre membre est obligatoire.
8. **Corriger** si le relecteur le demande, puis **fusionner** une fois l'approbation obtenue.
9. **Supprimer la branche** après la fusion (GitHub propose un bouton).

## 3. Nommer les branches

Format : `type/numéro-du-ticket-description-courte`, en minuscules, mots séparés par des tirets.

| Type | Quand l'utiliser | Exemple |
| --- | --- | --- |
| `feat` | Nouvelle fonctionnalité | `feat/12-barre-de-recherche` |
| `fix` | Correction d'un bug | `fix/18-carte-mobile` |
| `docs` | Documentation uniquement | `docs/7-readme-installation` |
| `data` | Données du campus (dépôt data) | `data/25-zone-z03` |
| `refactor` | Réorganisation du code sans changement visible | `refactor/30-service-lieux` |
| `chore` | Configuration, dépendances, outils | `chore/3-config-eslint` |

## 4. Écrire les messages de commit

Nous suivons la convention *Conventional Commits*, en français :

```
type(portée): description courte à l'impératif
```

- **type** : `feat`, `fix`, `docs`, `data`, `refactor`, `test`, `style`, `chore` ;
- **portée** (facultative) : la partie concernée, par exemple `carte`, `recherche`, `lieux`, `auth` ;
- **description** : 50 caractères environ, à l'impératif, sans point final.

Exemples :

```
feat(recherche): ajouter les suggestions pendant la saisie
fix(carte): corriger le zoom initial sur mobile
docs: expliquer l'installation de la base locale
data(z03): ajouter les lieux validés de la zone Z03
```

Un commit = une modification cohérente. On évite les messages vagues comme « modifs », « update » ou « ça marche ».

## 5. Les demandes de fusion (pull requests)

- **Petites** : une demande de fusion traite **un seul** ticket. Au-delà de 400 lignes modifiées environ, découpez.
- **Reliées au ticket** : écrire `Closes #12` dans la description ferme le ticket automatiquement à la fusion.
- **Vérifiées avant d'être proposées** : le projet compile, les tests passent, le lint ne signale pas d'erreur.
- **Avec une capture d'écran** pour tout changement visible dans l'interface.

## 6. Relire le travail des autres

Relire n'est pas une formalité : c'est la meilleure façon d'apprendre et d'éviter les erreurs. Le relecteur vérifie :

- [ ] le code fait ce que décrit le ticket ;
- [ ] il est lisible : noms clairs, pas de code mort, pas de duplication inutile ;
- [ ] il ne contient **aucun secret** (mot de passe, clé, fichier `.env`) ;
- [ ] les cas d'erreur sont gérés ;
- [ ] il a pu lancer le projet et tester la modification si elle est visible.

Les remarques sont **bienveillantes et précises** : on commente le code, jamais la personne. Une question vaut mieux qu'un reproche (« Que se passe-t-il si la liste est vide ? »).

Délai attendu : une demande de fusion reçoit une première relecture **sous 48 heures**.

## 7. Les règles de sécurité

- **Jamais de secret dans Git.** Les variables sensibles vont dans un fichier `.env`, qui est ignoré par Git. Le fichier `.env.example` liste les variables nécessaires, sans leurs valeurs.
- Si un secret a été poussé par erreur : prévenir immédiatement la coordination ; le secret doit être **changé**, le supprimer de Git ne suffit pas.
- **Aucune donnée personnelle** dans les dépôts (règle du cahier des charges, ENF-21).

## 8. Les tickets (issues)

Utilisez les modèles proposés : **Bug**, **Fonctionnalité** ou **Tâche**. Un bon ticket permet à n'importe quel membre de comprendre le travail sans poser de question : contexte, résultat attendu, critères de fin.

## 9. Besoin d'aide ?

Bloqué plus d'une heure ? Posez la question dans le groupe WhatsApp du projet ou en commentaire du ticket. Demander de l'aide tôt fait gagner du temps à tout le monde.
