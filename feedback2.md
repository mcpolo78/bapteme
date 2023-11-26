# Feedback apprenant 2

L'application se lance correctement 👍

## Page d'accueil : RAS 👍

## Details d'une carte

- l'ajout d'une carte au deck est OK 👍
- Il manque le nom de la carte en titre au dessus de la carte
- le lien [+] et le nom de la carte doivent apparaitrent dans l'image et pas en dessous 
- il manque les informations élément, valeurs et direction

## Decks 

- il manque le lien de suppression au deck :(
- on ne doit pas pouvoir ajouter + de 5 cartes au deck
- il y a un $ qui traine dans l'affichage ;)

## Recherche par éléments :

- aucun ne retourne pas de résultat alors qu'il y a pleins de cartes sans éléments ! =)
- ok pour les autres éléments, dommage que les images ne s'affichent pas, tu auraient pu réutiliser la vue pour lister les cartes ;-)
- prise en compte de l'accent pour l'élément "sacré", c'est bien
  
## Recherche par niveau, valeur, et nom :

- il fallait faire une fonction par recherche dans ton controller
- il fallait faire une route par recherche 

# Rappels / Correction

- ## SESSION_SECRET 

Dans le fichier index.js, la ligne suivante :

```
secret: 'dadp kdfpkazdf kaf   a*fka kfafâlfaflafelfafv lefa',
```

La valeur ne doit pas etre public ! par exemple si tu dépose le code sur ton repo perso, la clé sera visible, une bonne pratique est d'utiliser une constante dans le fichier d'environnement.
aussi, il est convenu de ne pas mettre d'espace, cela pourra te jouer des tours un jour

Tu doit plutot utiliser une varaiable d'environnement SESSION_SECRET comme ceci :

```
secret: process.env.SESSION_SECRET 
```

Pour utiliser la session de manière sécurisé coté serveur, on attend la valeur dans la variable d'environnement SESSION_SECRET, qui doit être défini dans ton fichier .env
Cela permet de ne pas exposer publiquement la valeur "secrète" pour la session. 

- ## Cartes sans éléments

Il fallait également pouvoir retrouver les cartes sans éléments, tu pouvais par exemple faire une fonction spécifique pour cela, avec la requete :

```
`SELECT * FROM "card" WHERE "element" IS NULL`
```

Ici il faut comprendre que l'on récupère les valeurs de element qui sont égal à 'NULL' en base de données avec le mot clé 'IS NULL'

# Avis

C'est pluôt encouragement comme parcours mais il faut continuer à travailler !

N'hésite pas à me solliciter si tu as des questions, si tu veux revoir une notion, un exemple etc, à n'immporte quel moment même en dehors des heures de cours :-))) 