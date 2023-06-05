![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# LAB | #Promets-moi un dîner

## Introduction

En raison de la nature asynchrone de JavaScript, les promesses et les rappels sont très importants. Les deux nous permettent de contrôler le flux des opérations et d'exécuter des tâches en séquence.

<p align="center">

<img src="https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-cover.png" alt="Lab Promise me dinner - final result" width="500" />

</p>

## Exigences

- Forker ce repo
- Cloner ce repo

## Soumission

Après avoir terminé, exécutez les commandes suivantes:

```shell
$ git add .
$ git commit -m "done"
$ git push origin master
```

Créez une Pull Request afin que vos TAs puissent vérifier votre travail.

## Instructions

### Itération 0 | Le code de départ

Nous vous avons fourni un code de départ :

- `javascript/data.js` - contient quatre tableaux avec des étapes pour préparer 4 plats différents : *purée de pommes de terre*, *steak*, *choux de Bruxelles* et *brocoli*.

- `javascript/getInstruction.js` - ccontient une fonction **`getInstruction`** qui **utilise des rappels (callbacks)** pour récupérer de manière asynchrone les étapes d'instruction pour n'importe quel plat. Il utilise `setTimeout` pour simuler une opération asynchrone.

  ```js
  getInstruction(food, step, callback, errorCallback)
  ```

  :exclamation: **Vous ne devez apporter aucune modification à ce fichier.**

  

- `javascript/obtainInstruction.js` - contient une fonction **`obtainInstruction`** qui **utilise des promesses** pour récupérer de manière asynchrone les étapes d'instruction pour n'importe quel plat. Il utilise également `setTimeout` pour simuler une opération asynchrone.

  ```js
  obtainInstruction(food, step)
  ```

  :exclamation: **Vous ne devez apporter aucune modification à ce fichier non plus.**

  

- `javascript/index.js` - dans ce fichier, nous avons laissé un exemple pour vous montrer comment le code devrait s'exécuter. Cependant, le code fourni n'utilise pas encore de rappels ou de promesses imbriqués, c'est pourquoi les étapes ne s'affichent pas dans le bon ordre. Votre tâche lors de la première itération sera de le faire correctement, mais nous en parlerons plus tard.

- `index.html` - contient une structure HTML de base nécessaire, donc il n'est pas nécessaire d'ajouter du code. Les fichiers JavaScript mentionnés précédemment sont déjà liés à `index.html`. Le fichier `data.js` se charge en premier pour s'assurer que les tableaux contenant les instructions sont déjà chargés et peuvent être utilisés dans les autres fichiers où nous en avons besoin.

  :exclamation: **Vous ne devez apporter aucune modification à ce fichier.**



### Désynchronisation

**Vous devez écrire votre code <u>uniquement</u> dans le fichier `javascript/index.js`.**

Maintenant, ouvrez le fichier et examinez le code de départ fourni. Le code fourni n'utilise pas de rappels imbriqués pour imposer une séquence d'exécution, c'est pourquoi les étapes ne s'affichent pas dans le bon ordre.

Allez-y et ouvrez la page `index.html` dans le navigateur. Remarquez comment les étapes de cuisson s'affichent dans le désordre.


<details>
  <summary><b>Capture d'écran</b></summary>

  ![Steps out of sync](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-out-of-sync.gif)

</details>



:exclamation: Avant de commencer à travailler sur l'Itération 1, commentez le code initial dans `javascript/index.js`.


<br>

## Itération 1 | Préparez la purée de pommes de terre avec des rappels

À l'aide de rappels imbriqués, affichez les étapes de cuisson pour préparer la purée de pommes de terre dans le bon ordre. Écrivez votre JavaScript dans le fichier `javascript/index.js` fourni. Encore une fois, n'oubliez pas de ne pas modifier le fichier `getInstruction`.js.

```javascript
// Iteration 1 - using callbacks
getInstruction('mashedPotatoes', 0, (step0) => {
  document.querySelector("#mashedPotatoes").innerHTML += `<li>${step0}</li>`
  // ... Your code here
    // ...
});
```

Après la dernière étape, vous devez afficher un `<li>` supplémentaire avec le texte : `Mashed potatoes are ready!` ("La purée de pommes de terre est prête !").


<details>
  <summary><b>Résultat attendu :</b></summary>

![Iteration 1 expected result](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-1-result.gif)

</details>



## Itération 2 | Préparez le steak avec des promesses

À l'aide de promesses et de l'instruction `then()`, affichez les directives pour afficher les instructions de cuisson pour le steak dans le bon ordre. Cette fois-ci, vous devrez appeler la fonction `obtainInstruction` qui renvoie une promesse en attente.

Continuez à travailler dans le fichier `javascript/index.js`. Vous ne devez pas modifier le fichier `obtainInstruction.js`.

```javascript
// Iteration 2 - using promises
obtainInstruction('steak', 0)
  .then( (step0) => {
    document.querySelector("#steak").innerHTML += `<li>${step0}</li>`
    //  ... Your code here
  })
  // ... Your code here
```

Après la dernière étape, vous devez afficher un `<li>` supplémentaire avec le texte : `Stake is ready!` ("Le steak est prêt !").

<details>
  <summary><b>Résultat attendu :</b></summary>

![Iteration 2 expected result](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-2-result.gif)

</details>



## Itération 3 | Préparez le brocoli avec async/await

À l'aide de promesses avec la syntaxe `async` et `await`, affichez les directives pour préparer les brocolis dans le bon ordre. Vous aurez besoin de la fonction `obtainInstruction` qui renvoie une promesse en attente.

```javascript
async function makeBroccoli() {
  // ... Your code here
}
```

Après la dernière étape, vous devez afficher un `<li>` supplémentaire avec le texte : `Broccoli is ready!` ("Le brocoli est prêt !").


<details>
  <summary><b>Résultat attendu :</b></summary>

![Iteration 3 expected result](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-3-result.gif)

</details>



## Bonus 1

Lorsque le plat spécifique est prêt à être servi (toutes les étapes sont répertoriées), supprimez l'attribut `hidden` de l'élément `<img />` qui représente le plat, de sorte que l'image s'affiche.

<details>
  <summary><b>Résultat attendu :</b></summary>

![Bonus Iteration 1 expected result](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-bonus-1-result.gif)

</details>

## Bonus 2

À l'aide de `Promise.all`, affichez les étapes de cuisson pour préparer les brocolis dans le bon ordre.

Après la dernière étape, vous devez afficher un `<li>` supplémentaire avec le texte : `Brussels sprouts are ready!` ("Les brocolis sont prêts !").

**Le résultat final devrait ressembler à ceci - avec toutes les étapes de cuisson affichées dans le bon ordre:**

![Bonus Iteration 2 expected result](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-bonus-2-result.gif)

<br>

**Bon codage !** :blue_heart:

<br>

## FAQs


<details>
  <summary>Je suis bloqué dans l'exercice et je ne sais pas comment résoudre le problème ni par où commencer.</summary>
  <br>


  Si vous êtes bloqué dans votre code et que vous ne savez pas comment résoudre le problème ou par où commencer, vous devriez prendre du recul et essayer de formuler une question claire sur le problème spécifique auquel vous êtes confronté. Cela vous aidera à cibler le problème et à développer des solutions potentielles.

  Par exemple, s'agit-il d'un concept que vous ne comprenez pas, ou recevez-vous un message d'erreur que vous ne savez pas comment résoudre ? Il est généralement utile de tenter de formuler le problème le plus clairement possible, en incluant les messages d'erreur que vous recevez. Cela peut vous aider à communiquer le problème à d'autres personnes et éventuellement obtenir de l'aide de vos camarades de classe ou de ressources en ligne.

  Une fois que vous avez une compréhension claire du problème, vous pourrez commencer à travailler vers la solution.

  [Retour en haut](#faqs)
</details>

<details>
  <summary>Comment utiliser <code>then()</code> et <code>catch()</code> avec les promesses ?</summary>

  <br>

  Lorsque vous travaillez avec des promesses ou une *fonction qui renvoie une promesse*, vous pouvez attacher la méthode `.then()` pour gérer la valeur résolue et la méthode `catch()` pour gérer la valeur de rejet éventuelle.

  Voici un exemple de l'utilisation de `.then()` et `.catch()` pour gérer une promesse simple :

  ```js
  myPromise
    .then((result) => {
      console.log(result);
    })
    .catch((error) => {
      console.log(error);
    })
  ```

  <br>

  Voici un exemple d'utilisation de `.then()` et `.catch()` pour gérer une promesse renvoyée par une fonction ou une méthode :

  ```js
  someAPI.getData()
    .then((result) => {
      console.log(result);
    })
    .catch((error) => {
      console.log(error);
    })
  ```

  <br>

  Si vous essayez d'exécuter plusieurs promesses en séquence, vous pouvez le faire en renvoyant une promesse à partir d'un bloc `.then()`. Exemple :

  ```js
  someAPI.getData()
      .then((result1) => {
          console.log(result1);
          return someAPI.getData();
       })    // Return another pending promise
      .then((result2) => { // Handle the returned promise
          console.log(result2);
      })
      .catch((error) => {
          console.log(error);
      })
  ```

  La première ligne `someAPI.getData()` lance une opération asynchrone qui renvoie une promesse. La méthode `.then()` est ensuite appelée sur la promesse pour gérer la valeur résolue.

  Le premier `then()` renvoie une autre promesse avec un autre appel à `someAPI.getData()`, ce qui permet de chaîner une autre fonction `then()` qui gère la deuxième valeur résolue, en l'affichant dans la console.

  <br>

  [Retour en haut](#faqs)

</details>

<details>
  <summary>Comment utiliser la fonction <code>async</code> et <code>await</code> ?</summary>

  <br>

  Vous créez une fonction asynchrone en utilisant le mot-clé `async` avant la définition de la fonction.

  Une fonction asynchrone vous permet d'utiliser le mot-clé `await` à l'intérieur du corps de la fonction pour attendre qu'une promesse soit résolue.

  Lorsque vous utilisez une fonction asynchrone pour gérer du code asynchrone (par exemple, un appel d'API) qui pourrait potentiellement générer une erreur, vous devez ajouter un bloc `try`/`catch` pour pouvoir gérer d'éventuelles erreurs.

  ##### Syntaxe

  ```js
  async function doSomething() {
    try {
      // Code that will be executed asynchronously
      // that might throw an error
    }
    catch (error) {
      // Handle the error
    }
  }
  ```

  <br>

  ##### Utilisation de `await` à l'intérieur d'une fonction `async`

  Voici un exemple d'utilisation de `await` à l'intérieur d'une fonction async pour attendre la résolution d'une promesse :

  ```js
  async function getData() {
    try {
      let response = await fetch('https://api.github.com/search/repositories?q=js');
      let data = await response.json();
      console.log(data);
    }
    catch (error) {
      // error
    } 
  }
  ```

  <br>

  Dans l'exemple ci-dessus, le premier `await` est utilisé pour attendre la résolution de la promesse renvoyée par `fetch()`. La valeur de la promesse résolue est ensuite assignée à la variable `response`.

  Le deuxième `await` est utilisé pour analyser la réponse en tant qu'objet JSON et attendre la résolution de la promesse renvoyée par `response.json()`. La valeur résolue est ensuite assignée à la variable `data`.

  La fonction utilise le mot-clé `return` pour renvoyer les `data` et permettre de consommer la valeur en dehors de la fonction.

  <br>

  ##### Une fonction `async` renvoie toujours une promesse

  La différence entre une fonction régulière et une fonction `async` est que la **fonction `async` renvoie toujours une promesse**.

  Une fois définie, vous pouvez appeler une fonction `async` comme une fonction régulière et gérer la promesse renvoyée à l'aide de `.then()` et `.catch()` ou `await`.

  <br>

  Voici un exemple d'utilisation de `then` et `catch` pour gérer une promesse renvoyée par une fonction `async` :

  ```js
  async function greeting() {
    // An `async` function always returns a promise
    // This value will be returned as a Promise
    return "HELLO IRONHACKERS!";
  }

  greeting()
    .then((result) => {
      console.log(result);
    })
    .catch((error) => {
      console.log("Error:", error);
    })
  ```

  <br>

  Voici un exemple de gestion de la même fonction `async`, cette fois en utilisant `await` :

  ```js
  async function greeting() {
    // Async function always returns a promise
    // This value will be returned as a Promise
    return "HELLO IRONHACKERS"!;
  }

  // We need another wrapper `async` function so that we can use `await`
  async function wrapperFunction() {
    try {
      const result = await greeting(
      console.log(result);
    }
    catch (error) {
      console.log("Error:", error);
    }
  }
  ```

  Notez que nous avons besoin d'une autre fonction `async` enveloppante pour pouvoir utiliser `await`.
  <br>

  [Retour en haut](#faqs)

</details>

<details>
  <summary>HoComment utiliser le bloc <code>try</code> / <code>catch</code> ?</summary>

  <br>

  Le bloc `try`/`catch` est utilisé pour gérer les erreurs qui se produisent pendant l'exécution d'un programme.

  Le bloc `try` contient le code qui peut générer une erreur, et le bloc `catch` contient le code qui traitera l'erreur.

  Voici un exemple d'utilisation du bloc `try`/`catch` :

  ```js
  try {
    // Code that might throw an error
  } catch (error) {
    // Handle the error
  }
  ```

  <br>

  Le bloc `try`/`catch` est généralement utilisé dans les fonctions `async` pour gérer du code asynchrone qui peut potentiellement générer une erreur.

  Voici un exemple d'utilisation d'un bloc `try`/`catch` dans une fonction `async` pour gérer une promesse :

  ```js
  async function doSomething() {

    try {
      // Code that might throw an error
      const result = await someAsyncFunction();
    }
    catch (error) {
      // Handle the error
      console.error(error);
    }
  }
  ```

  Dans l'exemple ci-dessus, le bloc `try` contient une opération asynchrone qui pourrait générer une erreur : `await someAsyncFunction()`. Si une erreur est générée, l'exécution passera automatiquement au bloc `catch`.

  <br>

  [Retour en haut](#faqs)

</details>

<details>
  <summary>Comment utiliser </code>Promise.all()</code> ?</summary>

  <br>

  La méthode `Promise.all()` est utilisée pour gérer plusieurs promesses en même temps. Voici comment elle fonctionne :



  1. `Promise.all()` prend un tableau de promesses en argument. Exemple :

     > ```js
     > Promise.all( [promise1, promise2, promise3] )
     > ```  

  2. **`Promise.all()` renvoie une promesse en attente**, que vous pouvez traiter avec `.then()` et `.catch()` ou avec `await`. Exemple :

     > ```js
     > Promise.all( [promise1, promise2, promise3] )
     > .then((result) => {})
     > .catch((error) => {})
     > ```

  3. **La promesse se résout avec succès uniquement si toutes les promesses d'entrée sont accomplies.** La valeur résolue est un tableau contenant les valeurs résolues des promesses d'entrée. Exemple :

     > ```js
     > Promise.all( [promise1, promise2, promise3] )
     > .then((values) => { // Resolved value is an array
     >  console.log("promise1 value: ", values[0] );
     >  console.log("promise2 value: ", values[1] );
     >  console.log("promise3 value: ", values[2] );
     > })
     > .catch((error) => {})
     > ```

  4. **Si au moins l'une des promesses d'entrée est rejetée, la promesse renvoyée est rejetée** avec une erreur et l'exécution passe au bloc `catch`.

  <br>


  ##### Traitement de `Promise.all()` avec `then()` / `catch()`

  Voici un exemple d'utilisation de `Promise.all()` et du traitement de la promesse renvoyée avec `.then()` et `.catch()` :

  ```js
  const promise1 = new Promise((resolve, reject) => {
    resolve("HELLO");
  })

  const promise2 = new Promise((resolve, reject) => {
    resolve("WORLD");
  })


  Promise.all( [promise1, promise2] )
    .then((values) => {
      console.log(values);
    })
    .catch((error) => {
      console.log(error);
    })
  ```

  Dans l'exemple ci-dessus, nous définissons deux nouvelles promesses, `promise1` et `promise2`, et utilisons `Promise.all()` pour les traiter en même temps.

  `Promise.all([promise1, promise2])` renvoie une nouvelle promesse qui est remplie avec un tableau de valeurs remplies à partir des promesses d'entrée (`promise1` et `promise2`). Nous avons nommé ce tableau `values`.

  <br>

  ##### Traitement de `Promise.all()` avec `await`

  Voici un autre exemple de traitement de `Promise.all()` et de la promesse retournée avec `await` :

  ```js
  const promise1 = new Promise((resolve, reject) => {
    resolve("HELLO");
  });

  const promise2 = new Promise((resolve, reject) => {
    resolve("WORLD");
  });


  async function handlePromiseAll() {
    try {
      const values = Promise.all( [promise1, promise2] );
      console.log(values);
    }
    catch (error) {
      console.log(error);
    }
  }

  handlePromiseAll()
  ```

  Dans l'exemple ci-dessus, nous définissons deux nouvelles promesses, `promise1` et `promise2`, comme précédemment, et utilisons `Promise.all()` pour les traiter en même temps.

  Lorsque nous travaillons avec `await`, nous avons également besoin d'une fonction `async`, ce qui explique la présence de la fonction `handlePromiseAll`.

  À l'intérieur de cette fonction, le mot-clé `await` est utilisé pour attendre que la promesse retournée par `Promise.all()` se résolve. La valeur résolue est assignée à la variable `values`.

  <br>

  [Retour en haut](#faqs)

</details>

<details>
  <summary>J'obtiens une erreur : "not defined". Comment puis-je la corriger ?</summary>

  <br>

  L'erreur "ReferenceError: variable n'est pas définie" en JavaScript se produit lorsque vous essayez d'accéder à une variable ou à une fonction qui n'a pas été définie ou qui est hors de portée.

  Pour corriger le problème, vérifiez que vous avez défini la variable ou la fonction que vous essayez d'utiliser et vérifiez l'orthographe pour vous assurer d'utiliser le bon nom.

  Si la variable ou la fonction est définie dans un autre fichier, assurez-vous que le fichier a été importé ou chargé correctement.
  
  <br>

  [Retour en haut](#faqs)

</details>

<details>
  <summary>Je ne peux pas pousser les modifications vers le dépôt. Que dois-je faire ?</summary>
  <br>

There are a couple of possible reasons why you may be unable to *push* changes to a Git repository:

1. **Vous n'avez pas validé vos modifications** : Avant de pouvoir pousser vos modifications vers le dépôt, vous devez les valider en utilisant la commande `git commit`. Assurez-vous d'avoir validé vos modifications et essayez de pousser à nouveau. Pour ce faire, exécutez les commandes terminal suivantes à partir du dossier du projet :
  ```bash
  git add .
  git commit -m "Your commit message"
  git push
  ```
2. **Vous n'avez pas la permission de pousser vers le dépôt** : Si vous avez cloné le dépôt directement à partir du dépôt principal d'Ironhack sans faire d'abord une Fork, vous n'avez pas d'accès en écriture au dépôt.
Pour vérifier à quel dépôt distant vous avez cloné, exécutez la commande terminal suivante à partir du dossier du projet :
  ```bash
  git remote -v
  ```
Si le lien affiché est le même que le dépôt principal d'Ironhack, vous devrez d'abord effectuer un fork du dépôt vers votre compte GitHub, puis cloner votre fork sur votre machine locale pour pouvoir pousser les modifications.

**Note**: Vous devriez faire une copie de votre code local pour éviter de le perdre dans le processus.

  [Retour en haut](#faqs)

</details>

