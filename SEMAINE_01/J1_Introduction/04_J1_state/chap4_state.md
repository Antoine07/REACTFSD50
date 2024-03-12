# React State

> **Note**
> Afin d'expliquer le concept d'un **state**, nous allons repasser temporairement sur l'écriture d'un composant en classe ES6 (qui l'intègrent nativement)
> Sachez que l'on peut toutefois utiliser un state dans un composant de fonction, mais cela nécessite d'aborder la notion des _hooks_, ce qui est prévu plus loin dans ce cours …

Un state permet d'ajouter un état LOCAL à un composant.

Il existe une autre propriété en React le **state** qui est **"mutable"**. On met à jour cette propriété à l'aide d'une autre méthode `setState`. Cette méthode compare la valeur initiale de la propriété avec la valeur qui a changé et `setState` effectue un delta; si ce delta a changé, React met à jour la valeur du state. Cette méthode sera toujours à utiliser pour mettre à jour le state :

```js
this.state = {
  a: 1,
  b: 2,
};
```

**Lecture du state** dans le code :

```js
this.state.a;
this.state.b;
```

Ne cherchez pas à mettre à jour le state d'une autre manière. Par exemple ce qui suit n'est pas la bonne méthode ceci ne mettra pas à jour le rendu :

```js
// ❌ Ne fonctionnera pas !
this.state.a = 2;
```

Pour mettre à jour le state vous devez utiliser la méthode `setState`, elle mettra à jour le rendu (re-exécution, avec les classes, de la méthode render de la classe).

**Mise à jour du state** : notez que la mise à jour ci-dessous n'écrase pas la valeur "b" du state que l'on a défini précédemment, elle met à jour uniquement la valeur "a" du state. React fait ce que l'on appelle un delta avec le state initial.

```js
// ✅ Correct
this.setState({ a: 11 });
```

En résumé :

- un accès possible au state avec :

```js
this.state.maValeur;
```

- Une fonction pour mettre à jour le state :

```js
this.setState({ maValeur: "nouvelle valeur" });
```

## 01 Exemple complet avec une classe

```jsx
class TestState extends React.Component {
  constructor(props) {
    super(props);

    // Déclaration d'un état local (state), comprenant un compteur `count` initialisé à 0
    this.state = {
      count: 0,
    };
  }

  render() {
    // un setTimeout ne s'exécute qu'une seule fois, c'est le re-render qui ré-exécutera le settimeout
    setTimeout(() => {
      // à chaque fois cela déclenche un re-render
      this.setState({ count: this.state.count + 1 });
      // ne déclenche pas de re-render
      // this.state.count++;
      console.log(this.state.count);
    }, 1000);

    return (
      <div>
        <p>Count: {this.state.count} </p>
      </div>
    );
  }
}

ReactDOM.createRoot(document.getElementById("root")).render(<TestState />);
```


## Approche fonctionnelle

:rocket: Pour définir un state également en ayant une approche fonctionnelle, il faudra faire appel à un Hook : useState

```jsx
const Clock = () => {
  const [timer, setTimer] = React.useState(new Date());

  const tick = () => {
    console.log(timer);
    setTimeout(() => setTimer(new Date()), time);
  };

  tick();

  return <p>{timer.toLocaleTimeString()}</p>;
};
```

## 02 Cats


1. Affichez le nom de chaque chat avec la première lettre dans une coleur à chaque fois différentes, pour réaliser cette fonction créez un bouton permettant de modifier la couleur.


Remarque aidez vous de l'exemple ci-dessous.

```html
<script type="text/babel">
  function App(props){
    const [color, setColor] = React.useState('')

    const handleColor = e => {
      // déclencher la modification de l'état de color au click
      setColor('red')
    }

    return (
      <div>
        <p style={ { color : color }}>Name du chat </p>
        <button onClick={handleColor} > Change color </button>
      </div>
    )
  }
<script>
```

```js
const catsData = [
  { name: 'Whiskers', age: 3, color: 'Gray and White' },
  { name: 'Luna', age: 2, color: 'Black' },
  { name: 'Simba', age: 4, color: 'Orange' },
  { name: 'Midnight', age: 1, color: 'Black' },
  { name: 'Bella', age: 5, color: 'Tabby' },
  { name: 'Gizmo', age: 2, color: 'Gray' },
  { name: 'Nala', age: 3, color: 'Beige' },
  { name: 'Oliver', age: 4, color: 'White and Brown' },
  { name: 'Cleo', age: 2, color: 'Calico' },
  { name: 'Max', age: 6, color: 'Tabby' }
];
```