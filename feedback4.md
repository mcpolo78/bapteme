# Feedback apprenant 4 

C'est dommage, erreur au lancement de l'application, attention au nom de la base de données !

Dans ton fichier .env, la constante PG_URL contient "tripletriad" au lieu de "triple_triad" ;-)

## Page d'accueil

- affichage des images, nom et lien ok 👍
- les images ne redirigenet pas vers le détail d'une carte
- le lien + d'ajout au deck ne fait rien

## Details d'une carte : KO

## Decks : KO

## Recherche : KO

# Rappels / Correction

- ## index.js

Il faut pouvoir garder dans la session les cartes ajouté dans le deck, pour cela on utilise :

```
const session = require('express-session');
app.use(session(
{
secret: process.env.SESSION_SECRET,
resave: true,
saveUninitialized: true
}
));
```

Pour utiliser la session de manière sécurisé coté serveur, on attend la valeur dans la variable d'environnement SESSION_SECRET, qui doit être défini dans ton fichier .env
Cela permet de ne pas exposer publiquement la valeur "secrète" pour la session.

Il faut également initialiser le deck vide avec le code suivant :

```
//middleware maison pour initialiser le deck
app.use((request, response, next) => {
//si la propriété deck de la session vaut undefined, on la crée
if (!request.session.deck) {
request.session.deck = []
}
//sinon, on fait rien ...
//et on passe la main au middleware suivant
next();
});
```

N'hésite pas revoir la correction des challenges de cette semaine sur les sessions ;)

- ## redirection des images

Dans le fichier cardList.ejs à la ligne suivante : 

```
<a href="#">
```

Ton lien hypertexte ne pointe sur rien, il faut le lier à la vue des détails d'une carte qu'il faut faire

- ## lien d'ajout au deck

Dans le fichier cardList.ejs à la ligne suivante : 

```
<a class="link--addCard" title="Ajouter au deck" href="#">[ + ]</a>
```

Ton lien hypertexte ne pointe sur rien, il faut le lier à la route qui ajoute une carte au deck

- ##  Details d'une carte
    Dans ton controller principal il faut une fonction qui récupère l'id de la carte, fait appel à la fonction qui récupère en base les infos de la carte puis appeler la vue à créer. 

- ## Deck

    Il faut créer un controller pour ton deck avec les fonctions d'affichage, d'ajout et suppression d'une carte

- ## Recherche

    Dans ton controller de recherche, il faut:
  - récupérer l'élément, le niveau, la valeur, direction ou nom depuis l'URL
  - récupérer en base les cartes qui ont le même élément, avec appel de la bonne fonction dans ton dataMapper.js
  - appel de la bonne vue qui listes toutes les cartes récupérés

# Avis

Trop peu de fonctionnalités, pas mal d'erreurs et d'incompréhensions, il ne faut pas hésiter à revior les challenges corrigés, poser des questions, demander d'autres exemples...ne pas lâcher !

N'hésite pas à me solliciter si tu as des questions, si tu veux revoir une notion, un exemple etc, à n'immporte quel moment même en dehors des heures de cours :-)))
