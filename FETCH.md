# FETCH

Imaginons que fetch soit une fonction de messager. Ce messager peut aller sur Internet via une URL, trouver des informations et les apporter.

Un exemple simple :

```
fetch('https://carburant-pas-cher.com/brest')
  .then(response => {
    // Le messager a trouvé quelque chose
    return response.json(); // On lui dit de prendre la réponse et de la transformer en quelque chose que nous pouvons utiliser, comme des mots ou des images.
  })
  .then(data => {
    // Maintenant, nous avons les mots ou les images et nous pouvons les utiliser !
    console.log(data);
  })
```

Imaginons maintenant que tu obtiens le nom de domaine www.triple-triad-deck-builder.com, et que tu upload ton projet sur l'hébergeur de ton choix (aws, gcp, azure, heroku, autres...).

Ton application peux devenir une API !

Prenons un exemple avec ta route :

```
 router.get('/card/:id', cardController.renderOneCard);
```

Apres une petite modification dans ton controller main de la fonction carteDetails :
au lieu de 

```
response.render('cardDetails', {card}); 
```
faire
```
response.status(200).json({ cardDetails: { card } }); 
//au lieu d'appeler la vue, retourner une réponse OK ( .status(200) ), avec les informations de la carte de manière lisible ( grace au .json()).
```

Si un collegue fait un fetch de ta route depuis son application :

```
fetch('https://triple-triad-deck-builder.com/card/5')
  .then(response => {
    return response.json(); 
  })
  .then(data => {
    console.log(data);
  })
```

Le console.log(data) affichera quelque chose comme :
```
{
  "cardDetails": {
      "card": {
        "id": 5,
        "name": "Incube",
        "element": null,
        "level": 1,
        "value_north": 2,
        "value_east": 3,
        "value_south": 1,
        "value_west": 5,
        "visual_name": "Incube.jpg"
      }
  }
}
```

Avec ces infos on peux reconstruire chaque carte depuis une autre application, sur mobile par exemple, sans avoir a refaire le code (ou presque) coté backend !

Aussi il faut que ton application soit configurée pour accepter les requetes externes.


En complément tu peux l'enrober dans un try catch pour la gestion des erreurs, et de manière asynchrone et plus lisible : 

```
async function demanderQuelqueChose() {
  try {
    const reponse = await fetch('https://www.quel-heure-est-il-chez-le-pere-noel.com');
    const donnees = await reponse.json();
    console.log(donnees);
  } catch (erreur) {
    console.error('Il y a eu un problème :', erreur);
  }
}

demanderQuelqueChose();
```

fetch permet également d'utiliser des options :

```
fetch(url, {
  method: 'POST', // Méthode HTTP, par défaut c'est GET
  headers: {
    'Content-Type': 'application/json' // En-têtes de la requête
  },
  body: JSON.stringify({ key: 'value' }) // Corps de la requête pour les méthodes qui en ont besoin (POST, PUT, etc.)
});
```

Cela te permettra autre que lire, de créer, mettre à jour, supprimer ce qui te plait...

Pour aller plus loin :
<https://developer.mozilla.org/fr/docs/Web/API/Fetch_API/Using_Fetch> <br>

<https://www.pierre-giraud.com/javascript-apprendre-coder-cours/api-fetch/>

Si tu le souhaites on pourra voir ensemble comment upload ton projet, le lier à un nom de domaine et le configurer, ce n'est pas très compliqué !