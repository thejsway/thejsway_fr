# Ajoutez des conditions

Jusqu'à présent, toutes les instructions de nos programmes (à l'exception des lignes de commentaires) étaient systématiquement exécutées. Nous allons voir comment enrichir ces programmes en y ajoutant des possibilités d'exécution conditionnelle.

## TL;DR

* L'instruction `if` permet d'exprimer une **condition**. Les instructions associées au `if` n'est exécuté que si la condition est vérifiée (vraie). Une **condition** est une expression dont l'évaluation produit une valeur **booléenne** (`true` ou `false`).

* Les instructions associées à une instruction `if` sont regroupées dans un **bloc de code** délimité par une paire d'accolades ouvrante et fermante. Pour plus de lisibilité, le contenu d'un bloc de code être **indenté** (décalé vers la droite) par rapport à l'instruction `if` à laquelle il est associé.

* Les opérateurs `===`, `!==`, `<`, `<=`, `>` et `>=` peuvent être utilisés pour comparer des nombres au sein d'une condition. Ils renvoient tous un résultat booléen.

* Associée à un `if`, l'instruction `else` permet d'exprimer une **alternative**. Selon la valeur de la condition, le bloc de code associé au `if` ou celui associé au `else` sera exécuté, mais jamais les deux. On peut imbriquer sans limite des instructions `if/else` à l'intérieur d'autres instructions `if/else`.

* Les opérateurs logiques `&&` (ET), `||` (OU) et `!` (NON) permettent de créer des conditions composées.

* L'instruction `switch` permet d'exécuter un bloc de code parmi plusieurs selon la valeur d'une expression.

## Exprimer une condition

Imaginons qu'on souhaite écrire un programme qui fasse saisir un nombre à l'utilisateur, puis qui affiche un message si ce nombre est positif. Voici l'algorithme correspondant.

```text
Saisir un nombre
Si ce nombre est positif
    Afficher un message
```

L'affichage du message ne doit avoir lieu que si le nombre est positif : on dit qu'il est soumis à une **condition**.

### L'instruction `if`

Voici comment ce programme se traduit en JavaScript.

```javascript
const nombre = Number(prompt("Entrez un nombre :"));
if (nombre > 0) {
    console.log(`${nombre} est positif`);
}
```

Lorsque le nombre saisi est positif, un message s'affiche dans la console. Si le nombre est négatif ou nul, on n'obtient aucun affichage. L'instruction `console.log()` n'est exécutée que si le nombre saisi est positif.

Vous venez de découvrir comment soumettre l'exécution d'une partie d'un programme à une condition grâce à l'instruction JavaScript `if`. La syntaxe de cette instruction est la suivante.

```text
if (condition) {
    // instructions exécutées quand la condition est vraie
}
```

La paire d'accolades ouvrante et fermante délimite le **bloc de code** associé à l'instruction `if`. Cette instruction représente un **test**. On peut la traduire par l'ordre suivant : "Si la condition est vraie, alors exécute les instructions contenues dans le bloc de code".

W> Lorsque le bloc de code ne contient qu'une seule instruction, les accolades ne sont pas obligatoires. Dans un premier temps, je vous conseille tout de même de les ajouter systématiquement.

La condition est toujours placée entre parenthèses après le `if`. Les instructions du bloc de code associé sont décalées vers la droite par rapport au `if`. Cette pratique est appelée l'**indentation** et permet de rendre le code source bien plus lisible. A mesure que vos programmes deviendront plus complexes (avec des `if` et d'autres instructions étudiées plus loin), leur indentation deviendra essentielle pour faciliter leur lisibilité. Quelle que soit la valeur d'indentation choisie (le plus souvent entre 2 et 4 espaces), il est indispensable de toujours bien indenter son code !

### La notion de condition

Une **condition** est une expression dont l'évaluation produit une valeur soit vraie, soit fausse : on parle de valeur **booléenne**.

I> Quand la valeur d'une condition est vraie, on dit que cette condition est **vérifiée**.

Nous avons déjà étudié les types **nombre** et **chaîne** : le type **booléen** fait également partie des types supportés par le langage JavaScript. Ce type n'a que deux valeurs possibles : `true` (vrai) et `false` (faux).

```javascript
if (true) {
    // la condition du if est toujours vraie
    // les instructions de ce bloc seront toujours exécutées
}
if (false) {
    // la condition du if est toujours fausse
    // les instructions de ce bloc ne seront jamais exécutées
}
```

Toute expression produisant une valeur booléenne (donc soit vraie, soit fausse) peut être utilisée comme condition dans une instruction `if`. Si la valeur de cette expression est `true`, le bloc de code associé au `if` sera exécuté.

On peut créer des expressions booléennes en utilisant les opérateurs de comparaison regroupés dans le tableau suivant.

|Opérateur|Signification|
|---------|----|
|`===`|Egal à|
|`!==`|Différent de|
|`<`|Inférieur à|
|`<=`|Inférieur ou égal à|
|`>`|Supérieur à|
|`>=`|Supérieur ou égal à|

Dans d'autres langages de programmation, les opérateurs d'égalité et d'inégalité  s'écrivent respectivement `==` et `!=`. JavaScript supporte également ces opérateurs, mais il vaut mieux utiliser `===` et `!==` ([plus de détails](https://developer.mozilla.org/fr/docs/Web/JavaScript/Les_diff%C3%A9rents_tests_d_%C3%A9galit%C3%A9)).

E> La confusion entre l'opérateur d'égalité `===` (ou `==`) et l'opérateur d'affectation `=` dans l'écriture d'une condition est une erreur très fréquente. Vous voilà prévenu(e) !

Modifions le programme d'exemple pour remplacer l'opérateur `>` par `>=` et modifier le message affiché.

```javascript
const nombre = Number(prompt("Entrez un nombre :"));
if (nombre >= 0) {
    console.log(`${nombre} est positif ou nul`);
}
```

Si le nombre 0 est saisi, le message s'affiche dans la console, ce qui signifie que la condition `(nombre >= 0)` a bien été vérifiée.

## Exprimer une alternative

Dans un programme, on souhaite fréquemment agir différemment selon que la condition soit vraie ou fausse.

### L'instruction `else`

Enrichissons notre programme d'exemple pour qu'il affiche un message adapté au nombre saisi par l'utilisateur.

```javascript
const nombre = Number(prompt("Entrez un nombre :"));
if (nombre > 0) {
    console.log(`${nombre} est positif`);
}
else {
    console.log(`${nombre} est négatif ou nul`);
}
```

Selon le nombre saisi, un message adapté est toujours affiché dans la console. Notre programme agit différemment selon que la condition `(nombre > 0)` soit vraie ou fausse : c'est ce que l'on appelle une **alternative**.

Une alternative s'exprime en JavaScript grâce à l'instruction `else` associée à un `if`. Voici sa syntaxe.

```javascript
if (condition) {
    // instructions exécutées quand la condition est vraie
}
else {
    // instructions exécutées quand la condition est fausse
}
```

On peut traduire une instruction `if/else` comme ceci : "Si la condition est vraie, alors exécute les instructions du bloc de code associé au `if`, sinon exécute celles du bloc de code associé au `else`".

L'instruction `if/else` permet de créer un **branchement logique** à l'intérieur d'un programme. Pendant l'exécution, les instructions exécutées seront différentes selon la valeur de la condition. Un seul des deux blocs de code sera pris en compte.

### Imbriquer des conditions

Notre programme d'exemple peut encore être enrichi pour afficher un message spécifique si le nombre saisi est nul. Pour cela, le code doit être modifié de la manière suivante.

```javascript
const nombre = Number(prompt("Entrez un nombre :"));
if (nombre > 0) {
    console.log(`${nombre} est positif`);
} else { // nombre <= 0
    if (nombre < 0) {
        console.log(`${nombre} est négatif`);
    } else { // nombre === 0
        console.log(`${nombre} est nul`);
    }
}
```

Ce programme affiche bien un message adapté au nombre saisi, y compris lorsque ce nombre est 0.

C'est maintenant qu'il faut faire appel à votre sens logique pour le comprendre. Si le premier bloc `else` est exécuté, c'est que le nombre saisi est soit négatif, soit nul, puisque la condition`(nombre > 0)` du premier `if` n'a dans ce cas pas été vérifiée. A l'intérieur de ce bloc `else`, on vérifie si le nombre est strictement négatif avec la condition `(nombre < 0)`. Si cette condition est fausse, alors le nombre est forcément égal à 0.

I> Les commentaires présents sur les lignes de chaque instruction else donnent des précisions sur la condition lorsque ce blocelse est exécuté. Ils sont optionnels mais aident à comprendre le code. Je vous conseille de vous entraîner à écrire ce genre de commentaires lorsque vous imbriquez des conditions.

Il est possible de représenter graphiquement l'exécution du programme précédent au moyen d'un **diagramme de flux** qui montre les différents cheminements possibles selon la valeur du nombre saisi.

![Diagramme de flux du programme d'exemple](images/chapter03-01.png)

Cet exemple nous montre que l'indentation permet de bien visualiser les différents blocs crées par les instructions `if/else`. Il n'y a pas de limite (si ce n'est la lisibilité du programme) au niveau de profondeur des imbrications.

On rencontre fréquemment le cas particulier où la seule instruction d'un bloc `else` est un `if` (le `else` éventuellement associé à ce `if` ne compte pas comme une seconde instruction). Dans ce cas, il est possible d'écrire ce `if`  sur la même ligne que le premier `else`, sans accolades ni indentation. Ainsi, notre programme d'exemple peut être réécrit de la manière suivante.

```javascript
const nombre = Number(prompt("Entrez un nombre :"));
if (nombre > 0) {
    console.log(`${nombre} est positif`);
} else if (nombre < 0) {
    console.log(`${nombre} est négatif`);
} else {
    console.log(`${nombre} est nul`);
}
```

## Créer des conditions composées

### L'opérateur logique ET

Supposons qu'on souhaite vérifier qu'un nombre est compris entre 0 et 100. Cela signifie que le nombre doit être à la fois supérieur à 0 et inférieur à 100. La condition "nombre compris entre 0 et 100" peut s'exprimer sous la forme de deux sous-conditions "nombre supérieur ou égal à 0" et "nombre inférieur ou égal à 100". Il faut que l'une ET l'autre de ces sous-conditions soient vérifiées.

I> L'expression `0 <= nombre <= 100` est mathématiquement exacte mais ne peut pas s'écrire de cette manière en JavaScript (ni dans la plupart des autres langages de programmation).

La traduction en JavaScript de cette condition donne le résultat suivant.

```javascript
if ((nombre >= 0) && (nombre <= 100)) {
    console.log(`${nombre} est compris entre 0 et 100`);
}
```

I> Les parenthèses entre les sous-conditions ne sont pas obligatoires. Cependant, je vous conseille de les ajouter systématiquement dans un premier temps pour mieux visualiser la structure des conditions et éviter d'éventuelles mauvaises surprises liées aux priorités des opérateurs.

L'opérateur `&&` (ET logique) s'applique à deux valeurs de type booléen. Son résultat est la valeur `true` uniquement si les deux valeurs auxquelles il s'applique valent `true`.

```javascript
console.log(true && true);   // Affiche true
console.log(true && false);  // Affiche false
console.log(false && true);  // Affiche false
console.log(false && false); // Affiche false
```

Le résultat ci-dessus constitue ce qu'on appelle la **table de vérité** de l'opérateur `&&`.

### L'opérateur logique OU

Imaginons maintenant qu'on souhaite vérifier qu'un nombre est en dehors de l'intervalle [0, 100]. Pour satisfaire à cette condition, ce nombre doit être inférieur à 0 OU supérieur à 100.

Traduit en JavaScript, cet exemple donne le résultat suivant.

```javascript
if ((nombre < 0) || (nombre > 100)) {
    console.log(`${nombre} est en dehors de l'intervalle [0, 100]`);
}
```

L'opérateur `||` (OU logique) s'applique à deux valeurs de type booléen. Son résultat est la valeur true si au moins une des deux valeurs auxquelles il s'applique vaut `true`. Voici la table de vérité de l'opérateur `||`.

```javascript
console.log(true || true);   // Affiche true
console.log(true || false);  // Affiche true
console.log(false || true);  // Affiche true
console.log(false || false); // Affiche false
```

### L'opérateur logique NON

Il existe un troisième opérateur logique qui permet d'inverser la valeur d'une condition : l'opérateur NON. Il s'écrit en JavaScript sous la forme d'un point d'exclamation `!`.

```javascript
if (!(nombre > 100)) {
    console.log(`${nombre} est inférieur ou égal à 100`);
}
```

Voici la table de vérité de cet opérateur.

```javascript
console.log(!true);  // Affiche false
console.log(!false); // Affiche true
```

## Exprimer un choix

Essayons d'écrire un programme qui conseille l'utilisateur sur la tenue à porter en fonction de la météo actuelle. Une première solution consiste à utiliser des instructions `if/else`.

```javascript
const meteo = prompt("Quel temps fait-il dehors ?");
if (meteo === "soleil") {
    console.log("Sortez en t-shirt");
} else if (meteo === "vent") {
    console.log("Sortez en pull");
} else if (meteo === "pluie") {
    console.log("Sortez en blouson");
} else if (meteo === "neige") {
    console.log("Restez au chaud à la maison");
} else {
    console.log("Je n'ai pas compris !");
}
```

Lorsqu'un programme consiste à déclencher un bloc d'opérations parmi plusieurs selon la valeur d'une expression, on peut l'écrire en utilisant l'instruction JavaScript `switch`.

```javascript
const meteo = prompt("Quel temps fait-il dehors ?");
switch (meteo) {
case "soleil":
    console.log("Sortez en t-shirt");
    break;
case "vent":
    console.log("Sortez en pull");
    break;
case "pluie":
    console.log("Sortez en blouson");
    break;
case "neige":
    console.log("Restez au chaud à la maison");
    break;
default:
    console.log("Je n'ai pas compris !");
}
```

Le comportement de ce programme est strictement identique à celui de la version précédente.

L'instruction `switch` déclenche l'exécution d'un bloc d'instructions parmi plusieurs possibles. Seul le bloc correspondant à la valeur de l'expression testée sera pris en compte. Sa syntaxe est la suivante.

```javascript
switch (expression) {
case valeur1:
    // instructions exécutées quand expression vaut valeur1
    break;
case valeur2:
    // instructions exécutées quand expression vaut valeur2
    break;
...
default:
    // instructions exécutées quand aucune des valeurs ne correspond
}
```

Il n'y a pas de limite au nombre de cas possibles. Le mot-clé `default`, à placer en fin de `switch`, est optionnel. Il sert souvent à gérer les cas d'erreurs, comme dans l'exemple ci-dessus.

E> Les instructions `break;` dans les blocs `case` sont indispensables pour sortir du `switch` et éviter de passer d'un bloc à un autre.
E>
E>     const x = "abc";
E>     switch (x) {
E>     case "abc":
E>         console.log("x vaut abc");
E>         // pas de break : on passe au bloc suivant !
E>     case "def":
E>         console.log("x vaut def");
E>         break;
E>     }

L'exécution de cet exemple affiche deux messages : `"x vaut abc"` (résultat attendu) mais aussi `"x vaut def"`.

## A vous de jouer !

C'est le moment de valider votre compréhension de ce chapitre ! Voici quelques recommandations pour réaliser ces exercices :

* Continuez à bien nommer vos variables en respectant les normes définies au chapitre précédent, et indentez systématiquement les blocs de code associés aux instructions `if`, `else` et `switch`.

* Essayez de trouver et d'écrire plusieurs solutions au problème posé, par exemple une solution utilisant l'instruction `if` et une autre utilisant le `switch`.

* Entraînez-vous à tester vos programmes aussi complètement que possible, sans avoir peur d'y trouver des erreurs. C'est un exercice très formateur.

### Jour suivant ([résultat à obtenir](http://codepen.io/bpesquet/pen/BpaWwy?editors=1102))

Ecrivez un programme qui fait saisir un nom de jour à l'utilisateur, puis affiche le nom du jour suivant. Les erreurs de saisie (jour incorrect) doivent être gérées.

### Comparaison de deux nombres ([résultat à obtenir](http://codepen.io/bpesquet/pen/jyOGmY?editors=1102))

Ecrivez un programme qui fait saisir deux nombres puis compare leurs valeurs et affiche un message approprié.

### Baccalauréat ([résultat à obtenir](http://codepen.io/bpesquet/pen/egYGGQ?editors=1102))

Ecrivez un programme qui fait saisir la moyenne d'un candidat puis affiche si ce candidat est recalé (moyenne inférieure à 10), reçu (moyenne entre 10 et 12) ou reçu avec mention (moyenne supérieure ou égale à 12).

### Valeurs finales

Examinez le programme JavaScript ci-dessous.

```javascript
let nb1 = Number(prompt("Entrez nb1 :"));
let nb2 = Number(prompt("Entrez nb2 :"));
let nb3 = Number(prompt("Entrez nb3 :"));

if (nb1 > nb2) {
    nb1 = nb3 * 2;
} else {
    nb1++;
    if (nb2 > nb3) {
        nb1 = nb1 + nb3 * 3;
    } else {
        nb1 = 0;
        nb3 = nb3 * 2 + nb2;
    }
}
console.log(nb1, nb2, nb3);
```

Avant de l'exécuter, tentez de prévoir les valeurs finales des variables `nb1`, `nb2` et `nb3` en fonction de leurs valeurs initiales et complétez le tableau ci-dessous.

|Valeurs initiales    |Valeur finale `nb1`|Value finale `nb2`|Valeur finale `nb3`|
|---------------------|-------------------|------------------|-------------------|
|`nb1=nb2=nb3=4`      |
|`nb1=4, nb2=3, nb3=2`|
|`nb1=2, nb2=4, nb3=0`|

Vérifiez vos prévisions en exécutant le programme.

### Nombre de jours du mois ([résultat à obtenir](http://codepen.io/bpesquet/pen/MJWEXP?editors=1102))

Ecrivez un programme qui fait saisir le numéro d'un mois (nombre entre 1 et 12) puis affiche le nombre de jours de ce mois. On ne tiendra pas compte des années bissextiles. Les erreurs de saisie doivent être gérées.

### Heure suivante ([résultat à obtenir](http://codepen.io/bpesquet/pen/JEjrzd?editors=1102))

Ecrivez un programme qui demande une heure à un utilisateur sous la forme de trois informations (heures, minutes, secondes). il affiche ensuite l'heure qu'il sera une seconde plus tard. Les erreurs de saisie doivent être gérées.

W> Ce programme est moins simple qu'il en a l'air : validez votre solution en la testant avec les entrées suivantes. Vous devez obtenir les résultats indiqués ci-dessous.
W>
W>    * 14h17m59s => 14h18m0s
W>
W>    * 6h59m59s => 7h0m0s
W>
W>    * 23h59m59s => 0h0m0s (minuit)
