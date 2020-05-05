# Créez vos premiers objets

Dans ce chapitre, vous allez découvrir les objets ainsi que leur fonctionnement en JavaScript.

## TL;DR

* Un **objet** est une entité qui possède des **propriétés**. Chaque propriété correspond à une paire clé/valeur. La clé est le nom de la propriété.

* La valeur d'une propriété peut être une donnée (nombre, chaîne, etc) ou bien une fonction. Dans ce cas, la propriété est appelée une méthode.

* En JavaScript, on peut créer un **objet littéral** en définissant ses propriétés à l'intérieur d'une paire d'accolades.

```js
const monObjet = {
  propriete1: valeur1,
  propriete2: valeur2,
  // ... ,
  methode1(/* ... */) {
    // ...
  },
  methode2(/* ... */) {
    // ...
  }
  // ...
};

monObjet.propriete1 = nouvelleVal; // Définit la nouvelle valeur de propriete1
console.log(monObjet.propriete1);  // Affiche la valeur de propriete1
monObjet.methode1(...);            // Appelle la méthode methode1()
```

* A l'intérieur d'une méthode, le mot-clé `this` représente l'objet sur lequel la méthode s'applique.

* JavaScript propose de nombreux objets prédéfinis, tels que `console` ou `Math`.

## Introduction

### C'est quoi, un objet ?

Prenons un exemple très concret : pensez à un stylo, ou regardez celui qui est peut-être devant vous. Étudions ce stylo : quelles sont ses caractéristiques ? Sa couleur d'écriture (bleu, noir, rouge...), son type (à encre, à bille, à mine...), son fabricant... Sans oublier le plus important : il permet d'écrire ! Notre stylo possède un certain nombre de propriétés qui le caractérisent.

Revenons à nos programmes : qu'est-ce qu'un objet informatique ? Tout comme ce stylo, un objet informatique est une **entité** qui possède des **propriétés**. Chaque propriété définit une caractéristique de l'objet. Une propriété peut être une information associée à l'objet (exemple : la couleur du stylo) ou une action (exemple : la capacité du stylo à écrire).

### Quel rapport avec la programmation ?

La **programmation orientée objet** (en abrégé POO) est une manière d'écrire des programmes en utilisant des objets. Quand on utilise la POO, on cherche à représenter le domaine étudié sous la forme d'objets informatiques. Chaque objet informatique modélisera un élément de ce domaine.

La POO modifie la manière dont un programme est écrit et organisé. Jusqu'ici, vous avez appris à créer des programmes plutôt basés sur des fonctions : c'est ce que l'on appelle parfois la [programmation procédurale](https://fr.wikipedia.org/wiki/Programmation_proc%C3%A9durale). Vous allez découvrir comment les écrire en utilisant des objets.

## JavaScript et les objets

Comme de nombreux autres langages, JavaScript permet de programmer en utilisant des objets : on dit que ce langage est orienté objet. Il vous fournit un certain nombre d'objets prédéfinis tout en vous permettant de créer les vôtres.

### Création d'un objet

Voici la représentation JavaScript d'un stylo à bille Bic qui écrit en bleu.

```js
const stylo = {
  type: "bille",
  couleur: "bleu",
  marque: "Bic"
};
```

En JavaScript, on peut créer un objet en définissant ses propriétés à l'intérieur d'une paire d'accolades :  `{...}`. Cette manière de créer des objets est appelée **syntaxe littérale**.

W> Le point-virgule `;` après l'accolade fermante est optionnel, mais il vaut mieux prendre l'habitude de l'ajouter systématiquement pour éviter certaines mauvaises surprises dans des cas particuliers.

Le code ci-dessus définit une variable nommée `stylo` dont la valeur est un objet : on dit aussi que `stylo` est un objet. Cet objet possède trois propriétés : `type`,  `couleur` et `marque`. Chaque propriété possède un **nom** et une **valeur**, et est séparée des autres par une virgule (sauf la dernière).

### Accéder aux propriétés d'un objet

Une fois l'objet créé, vous pouvez accéder à ses propriétés en utilisant la **notation pointée** : `monObjet.maPropriete`.

```js
const stylo = {
  type: "bille",
  couleur: "bleu",
  marque: "Bic"
};

console.log(stylo.type); // "bille"
console.log(stylo.couleur); // "bleu"
console.log(stylo.marque); // "Bic"
```

L'accès à une propriété d'un objet est une expression qui produit une valeur. On peut inclure ces accès dans d'autres expressions plus complexes. Voici par exemple comment afficher les caractéristiques du stylo en une seule ligne.

```js
const stylo = {
  type: "bille",
  couleur: "bleu",
  marque: "Bic"
};

// "J'écris avec un stylo bille bleu de marque Bic"
console.log(`J'écris avec un stylo ${stylo.type} ${stylo.couleur} de marque ${stylo.marque}`);
```

### Modifier un objet

Une fois un objet créé, on peut modifier les valeurs de ses propriétés avec la syntaxe `monObjet.maPropriete = nouvelleValeur`.

```js
const stylo = {
  type: "bille",
  couleur: "bleu",
  marque: "Bic"
};

// Modification de la propriété "couleur"
stylo.couleur = "rouge";

// "J'écris avec un stylo bille rouge de marque Bic"
console.log(`J'écris avec un stylo ${stylo.type} ${stylo.couleur} de marque ${stylo.marque}`);
```

JavaScript offre même la possibilité d'ajouter dynamiquement de nouvelles propriétés à un objet déjà créé.

```js
const stylo = {
  type: "bille",
  couleur: "bleu",
  marque: "Bic"
};

// Ajout de la propriété "prix"
stylo.prix = "2.5";

// "Mon stylo coûte 2.5 euros"
console.log(`Mon stylo coûte ${stylo.prix} euros`);
```

## Programmer avec les objets

La plupart des cours sur la programmation orientée objet utilisent des exemples qui modélisent des animaux, des voitures ou encore des comptes bancaires. Essayons plutôt quelque chose de plus amusant : programmer un mini-jeu de rôle en utilisant des objets.

> Ce thème est également utilisé dans [d'autres cours en ligne](https://openclassrooms.com/fr/courses/2913686-lancez-vous-dans-la-programmation-avec-ruby), dont je me suis en partie inspiré.

Dans un jeu de rôle, chaque personnage est défini par de nombreuses caractéristiques (qui diffèrent suivant le jeu). Voici par exemple l'écran d'information sur un personnage d'un jeu en ligne multijoueurs.

![Feuille de personnage](images/chapter06-04.png)

Plus modestement, nous allons modéliser un personnage de notre jeu en le dotant de trois caractéristiques :

* son nom,
* sa santé (nombre de points de vie),
* sa force.

### Création d'un personnage

Je vous présente Aurora, le premier personnage de notre jeu :

```js
const aurora = {
  nom: "Aurora",
  sante: 150,
  force: 25
};
```

Aurora est représentée par un objet `aurora` ayant trois propriétés : `nom`, `sante`  et `force`. Elles ont chacune une valeur et, ensemble, définissent **l'état** de notre personnage à un instant donné.

I> On remarque au passage que les propriétés d'un objet peuvent être de différents types. Un objet peut même avoir un autre objet comme propriété !

Aurora s'apprête à vivre une longue série d'aventures, dont certaines pourront modifier ses caractéristiques, comme dans l'exemple ci-dessous.

```js
const aurora = {
  nom: "Aurora",
  sante: 150,
  force: 25
};

// "Aurora a 150 points de vie et 25 en force"
console.log(`${aurora.nom} a ${aurora.sante} points de vie et ${aurora.force} en force`);

console.log("Aurora est blessée par une flèche");
aurora.sante = aurora.sante - 20;

console.log("Aurora trouve un bracelet de force");
aurora.force = aurora.force + 10;

// "Aurora a 130 points de vie et 35 en force"
console.log(`${aurora.nom} a ${aurora.sante} points de vie et ${aurora.force} en force`);
```

### La notion de méthode

Dans notre programme, on remarque que l'instruction `console.log(...)` qui affiche les caractéristiques du personnage est dupliquée, ce qui est une mauvaise chose. Voici comment faire mieux.

#### Ajout d'une méthode à un objet

Observez l'exemple ci-dessous.

```js
const aurora = {
  nom: "Aurora",
  sante: 150,
  force: 25
};

// Renvoie la description du personnage
function decrire(personnage) {
  return `${personnage.nom} a ${personnage.sante} points de vie et ${personnage.force} en force`;
}

// "Aurora a 150 points de vie et 25 en force"
console.log(decrire(aurora));
```

La fonction `decrire()` n'utilise que les propriétés d'un personnage, qui est passé en paramètre. Plutôt que de la définir de manière externe, nous pouvons l'ajouter à la définition de notre objet sous la forme d'une nouvelle propriété dont la valeur est une fonction.

```js
const aurora = {
  nom: "Aurora",
  sante: 150,
  force: 25,

  // Renvoie la description du personnage
  decrire() {
    return `${this.nom} a ${this.sante} points de vie et ${this.force} en force`;
  }
};

// "Aurora a 150 points de vie et 25 en force"
console.log(aurora.decrire());
```

Observez attentivement les différences avec le précédent exemple. L'objet `aurora`  possède à présent une nouvelle propriété nommée `decrire`. La valeur de cette propriété est une fonction qui renvoie la description du personnage sous forme textuelle. Le résultat de l'exécution est exactement le même que précédemment.

Une propriété dont la valeur est une fonction est appelée une **méthode**. Une méthode permet de définir une action pour un objet. On dit également qu'une méthode ajoute à cet objet un **comportement**.

#### Appel d'une méthode sur un objet

Intéressons-nous à la dernière ligne du programme précédent.

```js
console.log(aurora.decrire());
```

Pour obtenir la description d'un personnage, on utilise maintenant l'expression  `aurora.decrire()` plutôt que `decrire(aurora)`.  Cette différence est *essentielle* :

* `decrire(aurora)` appelle la fonction `decrire()` en lui passant l'objet `aurora` en paramètre. Dans ce cas, la fonction est externe à l'objet.

* `aurora.decrire()` appelle la fonction `decrire()` de l'objet `aurora`. Dans ce cas, la fonction fait partie de la définition de l'objet : il s'agit d'une méthode.

Pour appeler une méthode nommée `maMethode` sur un objet `monObjet`, on utilise la syntaxe `monObjet.maMethode()`.

W> Attention à ne pas oublier les parenthèses : elles sont obligatoires pour appeler une méthode sur un objet !

### Le mot-clé `this`

Observez maintenant le corps de la méthode  decrire()  de notre objet  aurora.

```js
const aurora = {
  nom: "Aurora",
  sante: 150,
  force: 25,

  // Renvoie la description du personnage
  decrire() {
    return `${this.nom} a ${this.sante} points de vie et ${this.force} en force`;
  }
};
```

Un nouveau mot-clé y apparaît : `this`. Il est défini automatiquement par JavaScript à l'intérieur d'une méthode et représente l'objet sur lequel la méthode a été appelée.

La méthode `decrire()` ne prend plus de personnage en paramètre : elle utilise `this`  pour accéder aux propriétés de l'objet sur lequel elle a été appelée.

### Les objets prédéfinis de JavaScript

Le langage JavaScript met à la disposition des programmeurs un certain nombre d'objets standards qui peuvent rendre de multiples services. Nous en avons déjà utilisé quelques-uns :

* L'objet `console` donne accès à la console pour y écrire des messages texte.

> `console` ne fait pas partie de la spécification officielle du langage, mais est disponible dans la plupart des environnements JavaScript, notamment les navigateurs web et la plate-forme Node.js.

* L'objet `Math` rassemble des fonctionnalités mathématiques. Par exemple, `Math.random()` renvoie un nombre aléatoire entre 0 et 1.

## A vous de jouer !

Les exercices ci-dessous vont vous permettre d'écrire vos premiers programmes à base d'objets.

### Ajout de l'expérience du personnage

Améliorez notre programme d'exemple en ajoutant une propriété `xp` qui représente les points d'expérience du personnage. Sa valeur initiale est 0. L'expérience du personnage doit apparaître dans sa description.

### Modélisation d'un chien

Complétez le programme suivant avec la définition d'un objet `chien`.

```js
// TODO : ajoutez ici la définition de l'objet chien

// "Crockdur est un mâtin de Naples mesurant 75"
console.log(`${chien.nom} est un ${chien.race} mesurant ${chien.taille} cm`);
  
// "Tiens, un chat ! Crockdur aboie : Grrr ! Grrr !"
console.log(`Tiens, un chat ! ${chien.nom} aboie : ${chien.aboyer()}`);
```

### Modélisation d'un compte bancaire

Ecrivez un programme qui crée un compte bancaire ayant les caractéristiques suivantes :

* Une propriété `titulaire` avec la valeur "Alex".
* Une propriété `solde` avec la valeur 0.
* Une méthode `crediter()` qui ajoute le montant (positif ou négatif) passé en paramètre au solde du compte.
* Une méthode `decrire()` qui renvoie la description du compte.

Affichez la description de cet objet, ajoutez 250 au solde, retirez 80, puis affichez la description finale.
