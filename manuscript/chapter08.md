# Manipulez les chaînes de caractères

Les programmes que vous écrirez utiliserons fréquemment des données sous forme de chaînes de caractères. Il est essentiel de se familiariser avec leur fonctionnement.

## TL;DR : en résumé

* Bien que les chaînes de caractères fassent partie des types JavaScript de base, elles disposent de certaines propriétés et méthodes qui fonctionnent comme pour des objets.

* La  propriété `length` renvoie le nombre de caractères composant la chaîne.

* Les chaînes de caractères sont **immuables** (*immutables*) en JavaScript. Une fois créée, la valeur d'une chaîne ne change jamais. Les méthodes appliquées sur une chaîne ne changent pas la valeur initiale, mais renvoient une nouvelle chaîne.

* Les méthodes `toLowerCase()` et `toUpperCase()` renvoient une nouvelle chaîne respectivement en majuscules ou en minuscules.

* On compare les valeurs de deux chaînes à l'aide de l"opérateur `===`, qui est sensible à la casse.

* Une chaîne de caractères peut être gérée comme un tableau de caractères identifiés par leur **indice**. L'indice du premier caractère est 0 et non pas 1. On peut parcourir une chaîne caractère par caractère avec une boucle `for` ou la récente boucle `for-of`.

* La méthode `Array.from()` permet de transformer une chaîne en un véritable tableau, qui peut ensuite être parcouru lettre par lettre avec la méthode `forEach()`.

* Il est possible de rechercher des valeurs dans une chaîne avec les méthodes `indexOf()`, `startsWith()` et `endsWith()`.

* La méthode `split()` décompose une chaîne en sous-parties délimité par un caractère séparateur.

## Rappels sur les chaînes de caractères

Récapitulons ce que nous savons déjà au sujet des chaînes de caractères :

* Une valeur de type chaîne (*string*) permet de représenter un texte.

* En JavaScript, on définit une chaîne en plaçant un texte entre guillemets simples ('je suis une chaîne') ou entre guillemets doubles ("je suis une chaîne"). Ce cours privilégie l'utilisation de guillemets doubles.

* On peut insérer dans une chaîne certains caractères spéciaux en utilisant le caractère `\` ("antislash" ou "backslash") suivi d'un autre caractère. Par exemple, `\n` définit un retour à la ligne.

* Appliqué à des chaînes de caractères, l'opérateur `+` déclenche la concaténation (jointure) des deux valeurs.

Outre ces possibilités de base, le type JavaScript chaîne dispose de nombreuses fonctionnalités. Nous allons maintenant étudier les principales opérations réalisables sur une chaîne de caractères.

## Obtenir la longueur d'une chaîne

Pour obtenir la longueur d'une chaîne (c'est-à-dire le nombre de caractères qui la composent, qu'on appelle également sa taille), il suffit de lui appliquer la propriété `length`. On obtient la longueur sous la forme d'une valeur entière.

```js
console.log("ABC".length); // 3
console.log("Je suis une chaîne".length); // 18
```

Bien entendu, `length` peut être appliqué sur des variables de type chaîne. Son résultat peut être stocké dans une variable en vue d'une utilisation ultérieure.

```js
const mot = "Kangourou";
const longueurMot = mot.length; // longueurMot contient la valeur 9
console.log(longueurMot); // 9
```

Rappel : la syntaxe qui consiste à utiliser un point (`.`) entre la chaîne de caractères et le mot `length` s'appelle la **notation pointée**.

## Convertir une chaîne en minuscules ou en majuscules

Une valeur de type chaîne peut être convertie en minuscules en lui appliquant la méthode `toLowerCase()`. De même, on peut lui appliquer `toUpperCase()` pour la convertir en majuscules. Ces méthodes renvoient toutes deux une nouvelle chaîne.

```js
const motInitial = "Bora-Bora";
console.log(motInitial.toLowerCase());  // "bora-bora"
console.log(motInitial.toUpperCase());  // "BORA-BORA"
console.log(motInitial);  // "Bora-Bora"
```

Il est essentiel de retenir que la chaîne initiale n'est pas modifiée par ces méthodes, ni par aucune autre méthode appelée sur une chaîne de caractères. Toutes les opérations applicables aux chaînes de caractères ne modifient JAMAIS la chaîne initiale, mais renvoient de nouvelles chaînes. Une fois créée, une chaîne de caractères JavaScript ne peut plus être modifiée. On dit qu'elle est **immuable** (en anglais : *immutable*).

## Comparer deux chaînes

La comparaison entre deux chaînes s'effectue avec l'opérateur `===`. Cette opération renvoie une valeur booléenne : `true` si les deux chaînes sont égales, `false` sinon.

```js
const chaine = "azerty";
console.log(chaine === "azerty"); // true
console.log(chaine === "qwerty"); // false
```

> Il existe un autre opérateur de comparaison, `==`, dont l'utilisation en JavaScript est généralement déconseillée.

Attention cependant : la comparaison entre chaînes est sensible à la casse (*case sensitive*). Cela signifie que la présence de majuscules ou de minuscules dans les chaînes intervient dans le résultat de leur comparaison. Deux chaînes contenant le même texte mais pas les mêmes minuscules/majuscules ne seront pas considérées comme égales.

```js
console.log("Azerty" === "azerty"); // false (à cause du A majuscule)
```

La conversion en minuscules ou en majuscules est souvent utilisée pour comparer une valeur saisie par l'utilisateur (donc comportant potentiellement des minuscules et/ou des majuscules) à une valeur prédéfinie.

```js
const valeurSaisie = "Quitter";
console.log(valeurSaisie === "quitter");  // false (à cause du Q majuscule)
console.log(valeurSaisie.toLowerCase() === "quitter");  // true
```

## Les chaînes comme ensembles de caractères

### Associer un caractère à son indice

Une chaîne de caractères peut être considérée comme un ensemble de caractères. Chaque caractère est identifié par un numéro, appelé son indice (index en anglais). Comme pour les tableaux,

* L'indice du premier caractère d'une chaîne est 0 et non 1 comme on aurait pu s'y attendre.
* L'indice du dernier caractère d'une chaîne ? Réponse : il est égal à la longueur de la chaîne - 1.

### Accéder à un caractère à partir de son indice

Pour accéder à un caractère d'une chaîne, on ajoute `[]` à la chaîne, en indiquant entre les crochets l'indice du caractère : `maChaine[monIndice]`.

```js
const sport = "Tennis-ballon"; // 13 caractères
console.log(sport[0]); // "T"
console.log(sport[6]); // "-"
console.log(sport[13]); // undefined (longueur dépassée)
```

### Parcourir une chaîne caractère par caractère

Nous savons maintenant accéder à un caractère d'une chaîne. Comment faire pour la parcourir lettre par lettre ?

Une première solution serait d'accéder successivement à chaque lettre.

```js
const prenom = "Odile"; // 5 caractères
console.log(prenom[0]); // "O"
console.log(prenom[1]); // "d"
console.log(prenom[2]); // "i"
console.log(prenom[3]); // "l"
console.log(prenom[4]); // "e"
```

Oui mais... Si la chaîne à parcourir contient plusieurs dizaines de caractères ?

Il faut trouver une meilleure solution pour répéter l'accès à chaque lettre de la chaîne. Répéter... Ça ne vous rappelle pas quelque chose ? Mais si, bien sûr : les boucles !

Nous allons donc écrire une boucle pour accéder successivement à chaque caractère. Il faut maintenant choisir entre un `while` et un `for`. J'espère que vous vous rappelez que le choix dépend essentiellement du nombre de tours. S'il est prévisible, la boucle `for` offre plus de simplicité (gestion automatique de l'incrémentation du compteur). Ici, le nombre de tours de boucle est égal au nombre de caractères de la chaîne, autrement dit sa longueur. Comme il est prévisible, nous choisissons la boucle `for`.

Voici la syntaxe à utiliser pour parcourir une variable chaîne nommée ici `maChaine` caractère par caractère.

```js
for (let i = 0; i < maChaine.length; i++) {
  // maChaine[i] renvoie le ième caractère de maChaine
  // ...
}
```

Le compteur de bouclei varie de 0 (indice du premier caractère de la chaîne) à longueur de la chaîne - 1 (indice du dernier). Lorsque la valeur du compteur devient égale à la longueur de la chaîne, le valeur de l'expression `i < maChaine.length` devient fausse et la boucle se termine. A l'intérieur de la boucle, l'expression `maChaine[i]` renvoie le caractère ayant l'indice `i` (on dit parfois : "le ième caractère").

Appliquons cette syntaxe à notre exemple précédent. Le code ci-dessous parcourt la variable `prenom` pour afficher chacun de ses caractères.

```js
const prenom = "Odile";
for (let i = 0; i < prenom.length; i++) {
  console.log(prenom[i]);
}
```

On obtient le même résultat qu'avec le parcours manuel, mais notre code s'adapte maintenant à n'importe quelle chaîne : on dit qu'il est plus *générique*.

Comme pour les tableaux, on peut utiliser la récente boucle `for-of` pour parcourir une chaîne caractère par caractère.

```js
const prenom = "Odile";
for (const lettre of prenom) {
  console.log(lettre);
}
```

Cette syntaxe est conseillée si l'indice des caractères n'est pas nécessaire dans le corps de la boucle.

## Autres opérations sur les chaînes

### Transformer une chaîne en tableau

La méthode `Array.from()` permet de transformer une chaîne en un véritable tableau, qui peut ensuite être parcouru lettre par lettre avec la méthode `forEach()`.

```js
const prenom = "Odile";
const tabPrenom = Array.from(prenom);
tabPrenom.forEach(lettre => {
  console.log(lettre);
});
```

### Rechercher dans une chaîne

Il arrive fréquemment qu'on souhaite rechercher des valeurs à l'intérieur d'une chaîne de caractères. JavaScript propose plusieurs solutions pour cela.

La méthode `indexOf()` prend en paramètre la sous-chaîne recherchée. Si cette valeur est présente dans la chaîne, elle renvoie l'indice de sa première occurrence. Sinon, elle renvoie -1. Cette méthode est sensible à la casse.

```js
const chanson = "Honky Tonk Women";
console.log(chanson.indexOf("onk")); // 1
console.log(chanson.indexOf("Onk")); // -1 (à cause du O majuscule)
```

Vous pouvez également utiliser les méthodes `startsWith()` et `endsWith()` pour rechercher une valeur au début ou à la fin de la chaîne. Ces deux méthodes renvoient  `true` ou `false` selon que la valeur soit trouvée ou non. Attention, elles sont également sensibles à la casse.

```js
const chanson = "Honky Tonk Women";

console.log(chanson.startsWith("Honk")); // true
console.log(chanson.startsWith("honk")); // false
console.log(chanson.startsWith("Tonk")); // false

console.log(chanson.endsWith("men")); // true
console.log(chanson.endsWith("Men")); // false
console.log(chanson.endsWith("Tonk")); // false
```

### Décomposer une chaîne en sous-parties

Une chaîne de caractères est parfois composée de plusieurs sous-parties séparées par un caractère particulier (point, tiret, point-virgule, etc). Dans ce cas, on peut obtenir toutes ces parties à l'aide de la méthode `split()`. Elle prend en paramètre le séparateur et renvoie un tableau contenant les sous-parties.

```js
const listeMois = "Jan,Fev,Mar,Avr,Mai,Jun,Jul,Aou,Sep,Oct,Nov,Dec";
const mois = listeMois.split(",");
console.log(mois[0]); // "Jan"
console.log(mois[11]); // "Dec"
```

## A vous de jouer !

C'est l'heure des exercices ! Pensez toujours aux consignes habituelles sur le nommage des variables, l'indentation et les tests (pour trouver d'éventuelles erreurs bien cachées).

### Nombre de voyelles

Ecrivez une fonction `compterVoyelles(...)` qui prend en paramètre une chaîne et renvoie son nombre de voyelles.

```js
// TODO : écrivez ici votre fonction

console.log(compterVoyelles("RadAr")); // 2
console.log(compterVoyelles("Tic et Tac")); // 3
console.log(compterVoyelles("Oasis Oasis Oh")); // 7
```

### Conversion en "leet speak"

Le [leet speak](https://fr.wikipedia.org/wiki/Leet_speak) est un argot d'informaticien dans lequel certaines lettres sont remplacées par d'autres. Le tableau suivant donne quelques-unes de ces correspondances.

|Lettre initiale|Lettre en *leet speak*|
|-|-|
|a|4|
|b|8|
|e|3|
|l|1|
|o|0|
|s|5|
|t|7|

Complétez le programme ci-dessous afin de coder le processus de conversion d'un mot en *leet speak*.

```js
// TODO : complétez ici le programme

console.log(convertirMotLeet("Hello World!")); // "H3110 W0r1d!"
console.log(convertirMotLeet("Noob")); // "N008"
console.log(convertirMotLeet("Hacker")); // "H4ck3r"
```

### Palindrome

Un [palindrome](https://fr.wikipedia.org/wiki/Palindrome) est un mot ou une phrase qu'on peut lire indifféremment dans les deux sens.

Complétez le programme ci-dessous pour vérifier si un mot est bien un palindrome, sans tenir compte de la casse.

```js
// TODO : complétez ici le programme

console.log(estPalindrome("RadAr")); // true
console.log(estPalindrome("KAYAk")); // true
console.log(estPalindrome("Bora-Bora")); // false
```

> Les solutions des exercices sont [consultables en ligne](https://github.com/thejsway/thejsway_fr-code).
