# Les Hooks 🎣

Dans ce chapitre, nous n'utiliserons pas la CRA systématiquement, mais nous allons appréhender la notion de Hooks dans des fichiers uniques. Nous reviendrons à la CRA par la suite.

L'approche fonctionnelle pour définir des composants impose l'utilisation des Hooks pour retrouver les fonctionnalités de React comme la gestion du state, le cycle de vie, par exemple.

```jsx
function App(props){
  return(
    <div>
      <p>{props.content}</p>
    </div>
  )
}

ReactDOM.render(
  <App content="Bonjour React" />,
  document.getElementById('root')
);
```

React a introduit des Hooks depuis la version 16.8.0, ils donnent par exemple la possibilité de gérer les states directement dans une fonction. Les Hooks permettent de rendre le code plus modulable et plus performant.

**Avantages:**

- Le hook `useState` permet de définir un state et sa fonction de mise à jour en même temps.
- Vous pouvez avoir plusieurs `useState` par composant.
- La fonction `setCount` est plus simple à appeler.

## Règles pour l'utilisation des Hooks

- 🚫 Vous ne devez pas appeler les Hooks dans des boucles.
- 🚫 Vous ne devez pas les appeler dans des conditions.
- 🚫 N'appelez pas les Hooks dans des fonctions imbriquées.
- 🚫 N'appelez pas les Hooks depuis des fonctions JavaScript.

En suivant ces règles, vous garantissez que les Hooks sont appelés dans le même ordre à chaque affichage du composant.

Il existe un plugin qui vous permettra de respecter ces règles lors du développement de votre application.

```bash
npm install eslint-plugin-react-hooks --save-dev
```

Théoriquement, dans create-react-app, ces règles sont bien vérifiées.

## La gestion du state avec des Hooks

Pour définir les states dans une fonction, vous utiliserez `useState`.

```jsx
const TestState = (props) =>{
  // Définition du state avec useState : 2 paramètres respectivement
  // 1. Variable pour le state.
  // 2. Fonction qui mettra à jour le state.
  const [count, setCount] = React.useState(0);

  return (
      <div>
        <p>Hello World {count}</p>
        <button onClick={() => setCount(count + 1)}>
          click me 🚀
        </button>
      </div>
    );
}

ReactDOM.render(
  <TestState />,
  document.getElementById('root')
);
```

**Avantages:**

- Le hook `useState` permet de définir un state et sa fonction de mise à jour en même temps.
- Vous pouvez avoir plusieurs `useState` par composant.
- La fonction `setCount` est plus simple à appeler.

## `useEffect`

Vous pouvez gérer le cycle de vie à l'aide du hook **useEffect**. Ce dernier sera exécuté lors du **montage** de l'élément dans le DOM et lorsque les ou un state (spécifique) **sera/seront modifié(s)**. Ce hook possède également une fonction dite de nettoyage qui sera exécutée dans le cas où le composant est démonté du DOM.

Le `useEffect` factorise les trois fonctions du cycle de vie suivantes : **componentDidMount**, **componentDidUpdate** et **componentWillUnmount**.

Voyez l'exemple qui suit :

```jsx
const Counter = () => {
  const [count, setCount] = React.useState(0);

  // Au montage la première fois.
  // Et dès que le state change.
  React.useEffect(() => {
    setTimeout(() => {
      console.log(`First message: You clicked ${count} times 🎉`);
    }, 1000);
  });

  // Au montage la première fois.
  // Dès que le state change.
  React.useEffect(() => {
    setTimeout(() => {
      console.log(`Second message: You clicked ${count} times 🌟`);
    }, 1000);
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me 🚀
      </button>
    </div>
  );
}
```

**Il y a un inconvénient** à cette approche car dès que l'on modifie le state, tous les Hooks useEffects sont appelés. Pour remédier à ce problème, vous pouvez cibler le state en deuxième paramètre de useEffect. Ainsi, si un state particulier est modifié, on ré-exécute uniquement le code du useEffect concerné :

```jsx
const Counter = () => {
  const [count1, setCount1] = React.useState(0);
  const [count2, setCount2] = React.useState(0);

  // Au montage uniquement.
  // Puis dès que le state count1 est modifié.
  React.useEffect(() => {
    setTimeout(() => {
      console.log(`First message: You clicked ${count1} times 🎲`);
    }, 1000);
  }, [count1]);

  // Au montage uniquement.
  // Puis dès que le state count2 est modifié.
  React.useEffect(() => {
    setTimeout(() => {
      console.log(`Second message: You clicked ${count2} times 🎲`);
    }, 1000);
  }, [count2]);

  return (
    <div>
      <p>You clicked {count1} & {count2} times</p>
      <button onClick={() => setCount1(count1 + 1)}>
        First 🎲
      </button>
      <button onClick={() => setCount2(count2 + 1)}>
        Second 🎲
      </button>
    </div>
  );
}
```

Dans certains cas, vous pouvez indiquer à React **de n'exécuter qu'une seule fois**, au montage (après le premier affichage), le code se trouvant dans useEffect. Il faudra alors passer en deuxième paramètre un tableau vide. Cela indique à React que votre **effet** (code dans useEffect) ne dépend d’aucune valeur issue d'un state (local), donc il n’a jamais besoin d’être ré-exécuté...

```jsx
useEffect(() => {

  // faire quelque chose au montage du composant React
  
}, []);
```

## Fonction de nettoyage de useEffect

Dans la fonction **useEffect**, nous pouvons également appeler une méthode pour faire quelque chose lorsque :

- Soit nous démontons le composant du DOM.
- Soit lorsque React nettoie les effets du rendu précédent. Dans ce cas, useEffect est lié à une/des variable(s) du state.

Vous pouvez implémenter ces fonctionnalités en définissant dans le premier paramètre de la fonction useEffect une fonction de retour. Voyez l'exemple qui suit :

```

jsx
useEffect(() => {

  return ()=> {
    // à chaque fois que active change de valeur & au démontage du composant
  }  
}, [active]);
```

Si on souhaite exécuter une fonction de nettoyage uniquement
>[!TIP]
> Utilisez un tableau vide comme second paramètre de `useEffect` pour garantir qu'il s'exécute uniquement au montage du composant.

```jsx
useEffect(() => {

  // faire quelque chose au montage du composant React
  
}, []);
```

**Remarque :**

Notez que c'est très pratique, par exemple, lorsqu'on doit se désabonner d'un service pour éviter les fuites mémoires.

### 01 Exercice Nettoyage (question)

1. Il manque quelque chose dans le code suivant pour que le compteur puisse se déclencher. Corrigez-le.

1. Que fait la fonction de nettoyage concrètement ?
   
>[!TIP]
> Pensez à vérifier le déclencheur du compteur dans le code.

```jsx
const App = () => {
    const [active, setActive] = React.useState(false);
    const [count, setCount] = React.useState(10);
    
    React.useEffect(() => {

        if( active && count > 0 )
            setTimeout(() => {
                setCount(count - 1);
            }, 1000);
        
        /*
            Ce mécanisme optionnel nettoie les effets du rendu. 
            Tout effet (changement des props ou state) peut renvoyer une fonction 
            qui se chargera de son propre nettoyage
        */
        return () => {
            if(count === 1) { 
                setActive(false); 
                setCount(10) ; 
            }
        }
    }, [count]);


    return (
        <div>
            { active === false && <button onClick={() => setActive(true)}>Go</button> }
            <p>{count}</p>
        </div>
    )
}

ReactDOM.render(
    <App />,
    document.getElementById('root')
);
```

## `useReducer`

`useReducer` doit s'utiliser lorsque le state d'un composant devient complexe.

Un `useReducer` possède un reducer qui permet de prendre un state et une action et de retourner un nouveau state.

Un reducer peut être schématisé comme suit :

![reducer](images/reducer.png)

Créez un fichier `useReducer.html` et testez le code ci-dessous :

```jsx
const initialState = {count: 0};

const reducer = (state, action) => {

  switch (action.type) {
    case 'incr':
      return {count: state.count + 1};
    case 'decr':
      return {count: state.count - 1};
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = React.useReducer(reducer, initialState);
  return (
    <>
      Counter : {state.count}
      <button onClick={() => dispatch({type: 'decr'})}>-</button>
      <button onClick={() => dispatch({type: 'incr'})}>+</button>
    </>
  );
}
```

Le code suivant permet de faire un conteneur qui ne crée pas d'élément HTML dans le DOM inutile.

```jsx
<>
</>
```

## 03 🧮 Exercice Calculator

Reprenez l'exercice du Challenge avec uniquement les options suivantes en utilisant un `useReducer` pour gérer l'état de vos states de votre composant. Le code sera à faire dans un fichier `index.html` comme d'habitude.

```txt
Resultat : 17 <- Affichage du résultat

Num1 : [2]  Num2 : [15] <--  deux champs texte pour saisir vos nombres

[+] <-- Additionner 
[*] <-- Multiplier 
[Reset]
```
>[!TIP]
> Utilisez `useReducer` pour simplifier la gestion de l'état dans votre composant Calculator.
