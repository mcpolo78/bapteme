# Feedback 3

L'application se lance correctement 👍

## Page d'accueil

- affichage des images ok
- l'image devait être clickable au lieu du lien avec le nom de la carte ;-)
- ajout au deck KO, "card is not defined"

## Details d'une carte

- meme erreur "card is not defined"

## Decks : KO

## Recherche : KO

# Rappels / Correction

- ## SESSION_SECRET

Dans le fichier index.js, la ligne suivante :

```
secret: 'shqhshjsqh suiuui siofioq',
```

La valeur ne doit pas etre public ! par exemple si tu dépose le code sur ton repo perso, la clé sera visible, une bonne pratique est d'utiliser une constante dans le fichier d'environnement.
aussi, il est convenu de ne pas mettre d'espace, cela pourra te jouer des tours un jour

Tu doit plutot utiliser une varaiable d'environnement SESSION_SECRET comme ceci :

```
secret: process.env.SESSION_SECRET
```
Pour utiliser la session de manière sécurisé coté serveur, on attend la valeur dans la variable d'environnement SESSION_SECRET, qui doit être défini dans ton fichier .env
Cela permet de ne pas exposer publiquement la valeur "secrète" pour la session.

- ##  Details d'une carte, erreur "card is not defined"

    Dans le fichier cardDetails.ejs, on veut afficher le détails d'une seul carte, donc pas besoin de faire de boucle.
    Aussi, tu essayes d'accéder aux propriétés de la carte avec la variable "card" alors que dans ton mainController la variable que tu transmets ne porte pas le meme nom, je te laisses trouver ;-) 

- ## Deck
  
Il faut un créer un controller pour ton deck avec sa vue, avec une limitations a 5 cartes, et la posibilité de retirer chaque carte du deck

- ## Recherche par élément

La page s'affiche correctement et la présentation est OK !
Malheureusement il y une erreur lorsque l'on essayes une recherche.

Ce qu'il fallait faire en plus de ce que tu commencé dans ton controller pour la recherche :
    - récupérer l'élément depuis l'URL (ok)
    - récupérer en base les cartes qui ont le même élément, avec appel de la bonne fonction dans ton dataMapper.js
    - appel de la bonne vue qui listes toutes les cartes récupérés

Appliquer cette recette pour les autres recherche !

# Avis

Trop peu de fonctionnalités, pas mal d'erreurs et d'incompréhensions, il ne faut pas hésiter à revior les exercices corrigés, poser des questions, demander d'autres exemples...ne pas lâcher !

N'hésite pas à me solliciter si tu as des questions, si tu veux revoir une notion, un exemple etc, à n'immporte quel moment même en dehors des heures de cours :-)))
