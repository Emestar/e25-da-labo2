# [e25-da-labo2](https://github.com/Emestar/e25-da-labo2/tree/main)

## Description

Une application démontrant les **listes de sélection dépendantes avec SQLAlchemy et PySide6**.
Le projet implémente une relation 1-à-N entre les universités et facultés, où la sélection d'une université met automatiquement à jour la liste des facultés disponibles.

<!--
## TP2

Énoncé:
[01_README_sujets_laboratoire.md](https://github.com/hrhouma1/Pyside6_Students_ORM_3/blob/main/evaluation/01_README_sujets_laboratoire.md)
[Système Universitaire](https://github.com/hrhouma1/Pyside6_Students_ORM_3/blob/main/evaluation/02_sujet_universite.md)

Exemple à suivre pour vous aider:
[Pyside6_Students_ORM_3](https://github.com/hrhouma1/Pyside6_Students_ORM_3/tree/main)
-->

## Installation

Pour l'environnement virtuel, nous avons utilisé Python `3.9.13`, mais une version plus récente devrait marcher.

```bash
# Créer l'environnement virtuel
python -m venv .venv

# Activer l'environnement
.\.venv\Scripts\activate  # Windows
# ou
source .venv/bin/activate  # Linux/Mac

# Installer les dépendances
pip install -r requirements.txt
```

Si `requirements.txt` ne marche pas, installez les dépendances manuellement.

```bash
pip install sqlalchemy
pip install pyside6
```

## Utilisation

```bash
# Lancez l'application
python main.py
```

### Au lancement

L'application vient avec ses propres données, grâce au fichier `universites_facultes.db`.
![launch.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/launch.jpg)

#### Démonstration

Ce bouton fait *presque* tout en 1 coup (excluant `supprimer` et ajouter des données).
Il va d'abord afficher toutes les statistiques courantes. (`Voir Statistiques`)
Il va sélectionner une université et une faculté et l'afficher. (`Afficher Sélection`)

![demo_01.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/demo_01.jpg)
![demo_02.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/demo_02.jpg)

#### Afficher Sélection

Pour utiliser le bouton "Afficher Sélection", il faut sélectionner une université et une faculté.
Sélectionner une université :
![select_university.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/select_university.jpg)

Puis, sélectionner une faculté parmie la liste de facultés fournie par l'université.
![select_faculte.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/select_faculte.jpg)

Cliquer sur le bouton pour afficher :
![affiche.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/affiche.jpg)

**Erreurs possibles :**

Si on clique sur le bouton sans sélection :
![if_affiche_without_faculte.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/if_affiche_without_faculte.jpg)

Si une université n'a pas de faculté, le bouton reste inactif et un message l'annonce en bas :
![select_universite_no_faculte.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/select_universite_no_faculte.jpg)

#### Ajouter Université

Pour ajouter une université, les données obligatoires sont :

- Nom obligatoire et unique
- Ville obligatoire
- Code obligatoire, unique, max 10 caractères
- Année optionnelle (si fournie, doit être > 1000)

Si on ne rentre pas une donnée obligatoire, un pop-up va informer l'utilisateur de l'erreur,
dans ce cas, si on laisse le formulaire vide :
![add_university_empty.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/add_university_empty.jpg)

Si on rentre une année > 1000, le pop-up va l'informer :
![add_university_low_annee.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/add_university_low_annee.jpg)

Ajoutée avec succès:
![add_university_succes.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/add_university_succes.jpg)

**Erreurs possibles :**

Si on rentre des noms d'une université déjà enregistrée (le nom et/ou le code) :
![add_university_already.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/add_university_already.jpg)

#### Ajouter Faculté

Pour ajouter une faculté, les données obligatoires sont :

- Nom obligatoire
- Code obligatoire, max 10 caractères
- Nombre d'étudiants >= 0
- Université parent obligatoire (doit exister)

Si on ne rentre pas une donnée obligatoire, un pop-up va informer l'utilisateur de l'erreur,
dans ce cas, si on laisse le formulaire vide :
![add_faculte_empty.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/add_faculte_empty.jpg)

Note : si on laisse les nombres d'étudiants vides, par défaut, l'application va mettre 0.

Ajoutée avec succès:
![add_faculte_succes.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/add_faculte_succes.jpg)

**Erreurs possibles :**

Si on rentre des noms d'une université déjà enregistrée (le nom et/ou le code) :
![add_university_already.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/add_university_already.jpg)

#### Voir Statistiques

En cliquant sur ce bouton, il affiche ceci :
![voir_stats.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/voir_stats.jpg)

#### Vider les Messages

Ce bouton permet de vider les messages accumulés dans la table du bas.
![vide.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/vide.jpg)

#### Supprimer

Ce bouton permet de supprimer une université (et ses facultés incluses) OU supprimer une faculté d'une université spécifique.
Pour sélectionner, il faut utiliser les dropboxes du haut.
(Si vous ne sélectionnez rien, une erreur pareille au `Afficher Sélection` va s'affiche.)

##### Supprimer une université

Pour supprimer une université, sélectionner __seulement une université__, laisser la sélection de la faculté sur "Choisir une faculté".
Après la sélection et avoir cliqué sur le bouton `Supprimer`, un pop-up de confirmation s'affiche:
![delete_01.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/delete_01.jpg)

Si confirmé, l'application confirme la surpression.
![delete_02.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/delete_02.jpg)

Pour voir si les facultés liées à l'université sont aussi supprimées, on peut utiliser le bouton `Voir Statistiques`.</br>
**AVANT**</br>
![voir_stats.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/voir_stats.jpg)
**APRÈS**</br>
![delete_03_proof.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/delete_03_proof.jpg)

##### BONUS: Supprimer une faculté

Pour supprimer une faculté, il faut d'abord sélectionner son université, puis sélectionner la faculté que vous souhaitez supprimer. Une pop-up va demander, pour la validation, de supprimer la faculté.
![delete_faculte.jpg](https://github.com/Emestar/e25-da-labo2/blob/natacha/documentation/img/delete_faculte.jpg)
