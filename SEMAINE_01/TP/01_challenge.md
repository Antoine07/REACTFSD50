# 01 Challenge

## Partie 0 

Révisez ce que nous avons vu, demain on vous posera des questions sous forme d'un QCM.

## Partie 1

Pour ce challenge vous utiliserez un fichier unique index.html en important l'ensemble des dépendances (liens).

:rocket: Utilisez le tableau suivant

```js
const numbers = [
   4, 14, 20, 6, 11, 12, 13,
   5, 16, 10, 3, 15,  2, 18,
  19,  8, 17, 1,  9,  7
]
```

1. Affichez ces valeurs dans le DOM à l'aide de React, centrez l'affichage des valeurs au centre de la page sur une ligne.

1. Améliorez le rendu avec des CSS.

1. Créez une petite horologe qui donne l'heure qui passe dans un header.

## Partie 2

1. Créez un bouton order pour ordonner la liste de manière croissante, puis décroissante au click.

1. Créez un bouton shuffle qui mélange les mots de la phrase.

## Partie 3 Facultative

1. Reprendre dans un fichier à part l'exercice précédent et affichez toutes les secondes les valeurs du tableau `numbers` ci-dessus, une fois les valeurs affichées, recommencez de manière cyclique. 

## Partie 4 (découverte)

1. Définissez un state phrase `const [phrase, setPhrase] = React.useState('')`

1. Créez un bouton **add** phrase qui ajoute la phrase à un tableau.

1. Mémorisez la phrase ci-dessous et affichez la dans la page.

```txt
Malheur à ceux qui se contentent de peu.
```

Comment faire : utilisez un champ input pour récupérer la phrase.

```js
// dans votre composant 

const handleChange = e => {
  const { value } = e.target
  // TODO set la phrase dans le state phrase
}

// le champ input est totalement contrôler par React avec le handleChange et la value 
<input type="text" onChange={handleChange} value={phrase} name="phrase" />
```
