# Feedback apprenant 1

C'est dommage, en lancant le projet il y a l'erreur suivante : "Error: secret option required for sessions".

Est-ce qu'il ne manquerait pas une constante dans le fichier d'environnement .env ? ;)

Sinon,

## Page d'accueil : RAS 👍

## Details d'une carte

- Il faut pouvoir ajouter la carte au deck depuis cette vue avec le lien [+]
- Il manque le nom de la carte dans l'image 
- Les informations auraient pu être affichées en français

## Decks : RAS 👍

## Recherche par éléments

- le résultat affiche 'NaN" au lieu de l'élément (petite erreur dans l'opération ternaire, un + en trop )
- l'élément "sacré" ne retourne aucun résultat (attention à l'accent ?)
  

## Recherche par niveau : RAS 👍

## Recherche par valeur + direction

- il fallait prendre en compte le "au moins" pour le niveau et afficher les niveaux supérieurs également

## Recherche par nom : RAS 👍

# Rappels / Correction

- ## SESSION_SECRET
  
Dans le fichier index.js, la ligne suivante : <br>

``` 
secret: process.env.SESSION_SECRET
``` 

Pour utiliser la session de manière sécurisé coté serveur, on attend la valeur dans la variable d'environnement SESSION_SECRET, qui doit être défini dans ton fichier .env
Cela permet de ne pas exposer publiquement la valeur "secrète" pour la session.

- ## Opération ternaire 

Dans le fichier searchController.js, la ligne suivante : 

```
title: 'Résultat de la recherche : ' + (searchedElement === 'null' ? ' sans élément' : + searchedElement),
```

Dans le cas ou la condition searchedElement === 'null', le titre sera 'Résultat de la recherche : ' + ' sans élément' = 'Résultat de la recherche : sans élément'

Sinon le titre sera 'Résultat de la recherche : ' + + searchedElement = NaN (bug car il ne comprends pas + +) 

J'espère que c'est plus clair !

# Avis

Globalement c'est bien, attention aux détails c'est souvent ce qui fais la différence ;-)