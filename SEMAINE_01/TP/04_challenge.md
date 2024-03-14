# 04 Challenge

## Partie 1 obligatoire

:rocket: Créez le projet "num-characters". Ensuite, vous devez inclure les dépendances suivantes dans le projet :

- `useReducer` pour gérer le store de l'application, que vous pouvez contextualiser.

L'application sera développée dans un fichier `index.html`. Vous pouvez utiliser Vite.js ; pour cela, consultez la documentation suivante : [Vite.js](./vite_command.md)

Vous devez gérer le store de votre application en utilisant **useReducer**.

L'application se présentera sur une page.

## Objectif de l'application

L'objectif de l'application est de permettre à l'utilisateur de saisir un texte, de définir un style pour ce texte et d'afficher ce texte avec son rendu juste en-dessous de la zone de saisie.

## Les fonctionnalités

Vous devez créer un formulaire permettant de saisir un texte.

Un bouton de sélection permettra de choisir un style de rendu pour le texte : `palevioletred` (choix par défaut) et `tomato`. Un autre champ permettra de sélectionner la taille du texte (un nombre compris entre 15px et 20px). Proposez les choix suivants : 15, 16, 17, 18, 19 et 20px.

Une fois que l'utilisateur a validé le formulaire, le texte est enregistré dans le store via votre `useReducer`. Chaque texte rendu peut être supprimé à l'aide d'un bouton de suppression.

- Wireframe pour saisir le texte et définir le style :

```
Saisir le texte : [ Bonjour tout le monde ]  

Sélectionnez un style de rendu : [ palevioletred ]

Taille du texte : [15]

[ Valider ]

---- Afficher le rendu sous la saisie ----

Texte 1 :

    [ Bonjour tout le monde ] 

    [ Supprimer ]
Texte 2 :

    [ Un autre texte avec un autre style de rendu ] 

    [ Supprimer ]
```

## Partie facultative 

Implémentez les fonctionnalités suivantes :

1. **Aperçu en direct du style** :
   - Ajoutez un aperçu en direct du texte avec le style sélectionné avant de valider le formulaire. Cela permettra à l'utilisateur de voir immédiatement l'effet de ses choix de style.

1. **Gestion des erreurs de saisie** :
   - Implémentez une gestion des erreurs pour indiquer à l'utilisateur si une saisie invalide a été effectuée, par exemple si aucun texte n'est saisi ou si la taille du texte est en dehors de la plage spécifiée.

1. **Options de style supplémentaires** :
   - Ajoutez la possibilité pour l'utilisateur de définir la couleur du texte en plus du style de fond. Cela pourrait être réalisé à l'aide d'un sélecteur de couleurs.

1. **Fonctionnalité de modification de texte** :
   - Permettez à l'utilisateur de modifier un texte rendu existant en cliquant dessus. Cela ouvrirait un champ de texte pré-rempli avec le texte existant et les paramètres de style actuels, lui permettant de modifier et de valider les changements.

1. **Options de personnalisation avancées** :
   - Offrez des options de personnalisation avancées telles que la police de caractères, l'espacement des caractères, l'alignement du texte, etc., pour permettre à l'utilisateur de personnaliser davantage l'apparence de son texte.

1. **Mode sombre/lumineux** :
   - Ajoutez un interrupteur pour activer un mode sombre ou lumineux dans l'interface utilisateur, offrant une expérience visuelle alternative en fonction des préférences de l'utilisateur.
