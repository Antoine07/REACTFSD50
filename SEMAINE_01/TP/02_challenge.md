# 02 sujet Challenge Calculatrice

Vous allez faire **une petite calculatrice** avec les notions, vous devez utiliser useState, useReducer. Et d'autre(s) Hook(s) si vous le souhaitez.

Vous êtes libre de faire cet exercice dans un fichier unique ou une application comme nous l'avons déjà vu précédemment.

Créez deux champs de saisi permettant de définir deux nombres pour la calculatrice. Puis créez les boutons suivants :

1. Un bouton + pour effectuer l'addition.

1. Un bouton X pour faire la multiplication.

1. Un bouton Reset pour effacer le résultat.

1. **Facultatif** gérez les messages d'erreur.

1. En utilisant le useEffect comptez le nombre d'opérations effectuées et affichez un message au bout de 10 calculs fait par l'utilisateur.

Implémentez également les boutons proposés dans le Wireframe ci-dessous.

```text

Resultat : 17 <- Affichage du résultat

Num1 : [2]  Num2 : [15] <--  deux champs texte pour saisir vos nombres

[+] <-- Additionner 
[*] <-- Multiplier 
[Reset]
[Enter]
```

Indications pour récupérez la valeur d'un champ texte dans le rendu, créez le state **number** avec sa fonction de mise à jour setNumber, pensez à tout maîtriser avec React lors de la récupération des données et de l'affichage de celles-ci dans l'élément HTML.

Dans l'exemple ci-dessous, le mieux étant de faire une fonction handleChange pour plus de lisibilité.

```js
<p>
  <input
    type="text"
    name="number"
    value={number}
    onChange={(e) => setNumber(e.target.value)}
  />
</p>
```

Aidez-vous de l'exemple de code que l'on a vu aujourd'hui pour gérer un formulaire.