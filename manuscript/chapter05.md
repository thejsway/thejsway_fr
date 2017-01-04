# Modularisez votre code avec les fonctions

Dans ce chapitre, vous allez découvrir comment décomposer un programme en sous-parties appelées des fonctions.

## TL;DR

TODO

## Introduction : le rôle des fonctions

Pour comprendre l'intérêt des fonctions, revenons sur notre algorithme de préparation d'un plat de pâtes issu du chapitre d'introduction.

Début

    Sortir une casserole

    Mettre de l'eau dans la casserole

    Mettre la casserole sur le feu

    Tant que l'eau ne bout pas

      Attendre

    Verser les pâtes dans la casserole

    Tant que les pâtes ne sont pas cuites

        Attendre

    Verser les pâtes dans une passoire

    Remuer la passoire pour faire couler l'eau

    Remettre les pâtes dans la casserole

    Goûter

    Tant que les pâtes sont trop fades

        Ajouter du sel

        Goûter

    Si on préfère le beurre à l'huile

        Ajouter du beurre

    Sinon

        Ajouter de l'huile

Fin

Voici le même algorithme. écrit d'une manière différente.

Début

    Faire bouillir de l'eau

    Cuire les pâtes dans l'eau

    Egoutter les pâtes

    Assaisonner les pâtes

Fin

La première version détaille toutes les actions individuelles à réaliser. La seconde décompose la recette en sous-étapes regroupant plusieurs actions individuelles. Cette version est plus concise et plus facile à interpréter, mais elle introduit des concepts relatifs au domaine de la cuisine comme cuire, égoutter, ou assaisonner. On peut envisager de réutiliser ces concepts pour réaliser d'autres recettes, par exemple la préparation d'un plat de riz.

Jusqu'à présent, vos programmes étaient écrits sur le modèle du premier algorithme : des actions individuelles qui s'enchaînent. Vous allez maintenant apprendre à les concevoir sous la forme d'un ensemble de sous-étapes. En JavaScript, ces sous-étapes sont appelées des fonctions.

## Découverte des fonctions

Une fonction est un regroupement d'instructions qui réalise une tâche donnée.

Voici un exemple basique utilisant une fonction.

function direBonjour() {

    console.log("Bonjour !");

}

console.log("Début du programme");

direBonjour();

console.log("Fin du programme");

Tapez cet exemple dans le fichiercours.js situé dans le répertoirechapitre_5/js (à créer). Créez ensuite le fichiercours.html associé danschapitre_5/html, puis ouvrez ce fichier dans Firefox. Vous obtenez le résultat suivant.

Les paragraphes suivants vont permettre d'expliquer ce résultat.

### Déclaration d'une fonction

Observons la première partie du programme d'exemple.

function direBonjour() {

    console.log("Bonjour !");

}

Cet extrait permet de créer une fonction nomméedireBonjour(). Elle n'est constituée que d'une seule instruction qui affiche sur la console le message "Bonjour !".

L'opération de création d'une fonction s'appelle la déclaration. Voici sa syntaxe.

// Déclaration d'une fonction nommée maFonction

function maFonction() {

    // Instructions de la fonction

}

La déclaration d'une fonction s'effectue à l'aide du mot-clé JavaScriptfunction suivi du nom de la fonction et d'une paire de parenthèses. Les instructions qui composent la fonction constituent le corps de la fonction. Ces instructions sont placées entre accolades et indentées.

### Appel d'une fonction

Voici la seconde partie de notre programme d'exemple.

console.log("Début du programme");

direBonjour();

console.log("Fin du programme");

La première et la troisième instructions affichent des messages dans la console.  La deuxième effectue un appel à la fonctiondireBonjour() déclarée plus haut.

Le débogage permet d'observer ce qui se produit lors de l'exécution du programme.
Télécharger la vidéo

L'appel d'une fonction s'effectue en écrivant le nom de la fonction suivi d'une paire de parenthèses. 

// ...

maFonction(); // Appel de la fonction maFonction

// ...

L'appel d'une fonction déclenche l'exécution des instructions qui la constituent, puis l'exécution reprend à l'endroit où la fonction a été appelée. Ce fonctionnement est illustré par le schéma ci-dessous.
Mécanisme d'appel d'une fonction
Mécanisme d'appel d'une fonction

### Avantages des fonctions

Lorsqu'on cherche à résoudre un problème complexe, il est généralement efficace de le décomposer en sous-problèmes plus simples. 

Les fonctions permettent d'appliquer ce principe à la création de logiciels : on va décomposer le programme en écrivant plusieurs fonctions, chacune dédiée à un objectif particulier. Le programme fera appel aux fonctions au fur et à mesure de son exécution.

Ecrit sous la forme d'une combinaison de fonctions, le programme sera plus lisible et plus facile à faire évoluer qu'un programme écrit de manière monobloc. De plus, il sera parfois possible de réutiliser certaines fonctions dans d'autres programmes.

Enfin, la création d'une fonction permet de lutter contre la duplication de code : plutôt que de dupliquer le même code dans un programme, on centralise ce code sous la forme d'une fonction et on y fait appel depuis tous les endroits où c'est nécessaire.

## Possibilités des fonctions

### Valeur de retour

Voici une variante de notre programme d'exemple.

function direBonjour() {

    return "Bonjour !";

}


console.log("Début du programme");

var resultat = direBonjour();

console.log(resultat);

console.log("Fin du programme");

Testez cette variante : vous obtenez exactement le même résultat que précédemment.

Dans cet exemple, le corps de la fonctiondireBonjour() a été modifié : l'instructionconsole.log("Bonjour !") a été remplacée par la lignereturn "Bonjour !".

L'utilisation du mot-cléreturn dans une fonction permet de lui donner une valeur de retour. Son appel produit un résultat qui correspond à la valeur placée juste après lereturn dans la fonction. Ce résultat peut être récupéré par le programme appelant. Ici, la fonctiondireBonjour() renvoie la valeur chaîne"Bonjour !". Cette valeur est stockée par le programme dans la variableresultat, qui est ensuite affichée.

Une fonction incluant une instructionreturn renvoie une valeur de retour lorsqu'elle est appelée : l'expression située immédiatement après lereturn.

// Déclaration d'une fonction nommée maFonction

function maFonction() {

    // Calcul de la valeur de retour

    // ...

    return valeurRetour;

}


// Récupération de la valeur de retour de maFonction

var valeur = maFonction();

// ...

Cette valeur de retour peut être de n'importe quel type (nombre, chaîne, etc). En revanche, une fonction ne peut renvoyer qu'une seule valeur.

Rien n'oblige à récupérer la valeur de retour d'une fonction, mais dans ce cas, cette valeur est "oubliée" par le programme qui appelle la fonction !

Si on essaie de récupérer la valeur de retour d'une fonction qui n'inclut pas d'instructionreturn, on obtient la valeur JavaScriptundefined.

function maFonction() {

    // Pas d'instruction return

}


var resultat = maFonction();


console.log(resultat); // Affiche undefined

Une fonction qui ne renvoie pas de valeur est parfois appelée une procédure.

L'exécution de l'instructionreturn renvoie immédiatement vers le programme appelant. Il ne faut jamais ajouter d'instructions après unreturn dans une fonction : elles ne seraient jamais exécutées.

On peut simplifier un peu notre exemple en affichant directement le résultat de l'appel à la fonctiondireBonjour() sans utiliser de variable. Ici, la valeur de retour dedireBonjour() est directement affichée dans la console.

function direBonjour() {

    return "Bonjour !";

}


console.log(direBonjour()); // Affiche "Bonjour !"

### Variables locales

Il est possible de déclarer des variables à l'intérieur d'une fonction, comme dans l'exemple ci-dessous.

function direBonjour() {

    var message = "Bonjour !";

    return message;

}


console.log(direBonjour());

La fonctiondireBonjour() déclare une variable nomméemessage, puis renvoie sa valeur.

Les variables déclarées dans le corps d'une fonction sont appelées des variables locales. En effet, elles ne sont utilisables qu'à l'intérieur de la fonction. Ainsi, l'exécution du programme suivant provoquera une erreur.

function direBonjour() {

    var message = "Bonjour !";

    return message;

}


console.log(direBonjour());

console.log(message); // Erreur : la variable message n'existe pas ici

A chaque appel d'une fonction qui déclare des variables locales, ces variables sont recréées. On peut donc appeler plusieurs fois la même fonction, et chaque appel sera parfaitement indépendant des autres.

On nomme portée d'une variable l'ensemble des endroits où elle est accessible. La portée d'une variable locale se limite au corps de la fonction dans laquelle elle est déclarée.

Ne pas pouvoir utiliser de variables locales en dehors des fonctions où elles sont déclarées peut sembler une limitation. C'est au contraire un double avantage :

    Une fonction peut être conçue comme une entité autonome et réutilisable.

    Un programme peut déclarer ses propres variables et utiliser autant de fonctions que nécessaire, sans se préoccuper des variables locales qui y sont déclarées. 

### Passage de paramètres

Un paramètre est une information dont une fonction a besoin pour jouer son rôle. Les paramètres d'une fonction sont définis entre parenthèses juste après le nom de la fonction. On peut ensuite utiliser leur valeur dans le corps de la fonction. 

La valeur d'un paramètre est fournie au moment de l'appel de la fonction : on dit que cette valeur est passée en paramètre. On appelle argument la valeur donnée à un paramètre lors d'un appel.

Modifions notre exemple pour construire un message de bienvenue personnalisé. 

function direBonjour(prenom) {

    var message = "Bonjour, " + prenom + " !";

    return message;

}


console.log(direBonjour("Baptiste"));

console.log(direBonjour("Sophie"));

La déclaration de la fonction ‌direBonjour() a été modifiée : elle contient à présent un paramètre nommé prenom. Testez ce programme : vous obtenez le résultat suivant.

Une fois de plus, le débogage va nous permettre de comprendre le résultat.
Télécharger la vidéo

Dans cet exemple, le premier appel à la fonctiondireBonjour() est fait avec l'argument"Baptiste" et le second avec l'argument"Sophie". Dans le premier cas, le paramètreprenom reçoit la valeur"Baptiste" et dans le second, la valeur"Sophie".

Les paramètres d'une fonction sont parfois appelés des paramètres formels et les arguments des paramètres effectifs. Pour des raisons de simplicité, je préfère employer les termes de paramètre et d'argument.

Voici la syntaxe générale de la déclaration d'une fonction acceptant des paramètres. Leur nombre n'est pas limité, mais il est rarement nécessaire de dépasser 3 ou 4 paramètres.

// Déclaration de la fonction maFonction

function maFonction(param1, param2, ...) {

    // Instructions pouvant utiliser param1, param2, ...

}


// Appel de la fonction maFonction

// param1 reçoit la valeur de arg1, param2 la valeur de arg2, ...

maFonction(arg1, arg2, ...);

Lors d'un appel à une fonction acceptant des paramètres, le nombre et l'ordre des paramètres doivent être respectés. Observez l'exemple suivant et le résultat de son exécution.

function presentation(prenom, age) {

    console.log("Tu t'appelles " + prenom + " et tu as " + age + " ans");

}


presentation("Garance", 7); // OK

presentation(3, "Prosper"); // Erreur : inversion !

Lors du second appel, les valeurs données aux paramètres sont inversées :prenom reçoit la valeur 3 etage reçoit la valeur"Prosper".

## Utilisation de fonctions anonymes

TODO

## Comment (bien) programmer avec les fonctions

### Créer des fonctions à bon escient

Une fonction peut utiliser les mêmes éléments qu'un programme classique : variables, conditions, boucles, etc. Une fonction peut même faire appel à une autre fonction, ce qui ouvre des possibilités infinies pour construire nos programmes.

Il convient toutefois de rester raisonnable et de ne pas multiplier artificiellement le nombre de fonctions d'un programme, sous peine de compliquer sérieusement sa compréhension (c'est le syndrome du code spaghetti). Il vaut mieux essayer de créer des fonctions ayant chacune un rôle bien défini et minimiser les interdépendances entre fonctions.

### Utiliser les fonctions prédéfinies de JavaScript

Sans les nommer ainsi, nous avons déjà utilisé plusieurs fonctions prédéfinies de JavaScript commeprompt() oualert(). Le langage vous propose un nombre important de fonctions qui répondent à des besoins variés. En programmation comme ailleurs, il est rarement utile de réinventer la roue et il est important de privilégier l'utilisation de ces fonctions existantes plutôt qu'une réécriture manuelle. 

La seule exception à cette règle est d'ordre pédagogique : apprendre à "faire comme" est souvent formateur.

Voici un exemple utilisant deux des nombreuses fonctions mathématiques offertes par JavaScript.

console.log(Math.min(4.5, 5)); // Affiche 4.5

console.log(Math.min(19, 9)); // Affiche 9

console.log(Math.min(1, 1)); // Affiche 1


console.log(Math.random()); // Affiche un nombre aléatoire entre 0 et 1

La fonctionMath.min() renvoie le minimum des nombres passés en paramètres. La fonctionMath.random() génère un nombre aléatoire entre 0 et 1.

Nous découvrirons d'autres fonctions prédéfinies dans la suite de ce cours.

### Limiter la complexité des fonctions

Le corps d'une fonction doit garder un niveau de complexité faible et ne pas être trop long. Il n'y a pas de maximum universel, mais au-delà d'une vingtaine de lignes de code, la question de la décomposition d'une fonction en sous-fonctions doit se poser.
Bien nommer fonctions et paramètres

Comme pour les variables, le nommage des fonctions et des paramètres joue un rôle important dans la lisibilité du programme. Les recommandations sont les mêmes : choisir des noms qui expriment précisément le rôle et respecter la norme camelCase.

S'il est difficile de trouver un nom pertinent pour une fonction, c'est sans doute que son rôle n'est pas bien défini et que sa création doit être remise en cause.

## A vous de jouer !

Créez ces exercices dans le répertoirechapitre_5.
Bonjour amélioré (résultat à obtenir)

Complétez le programmebonjour.js ci-dessous pour qu'il fasse saisir le prénom et le nom de l'utilisateur dans deux variables, puis affiche le résultat de l'appel à la fonctiondireBonjour().

// Renvoie un message de bienvenue

function direBonjour(prenom, nom) {

    var message = "Bonjour, " + prenom + " " + nom + " !";

    return message;

}


// TODO : faire saisir le prénom et le nom de l'utilisateur

// TODO : appeler direBonjour() avec les bons arguments et afficher son résultat

Carré d'un nombre (résultat à obtenir)

Complétez le programmecarre.js ci-dessous pour que la fonctioncarre() renvoie le carré d'un nombre passé en paramètre. 

// Renvoie le carré d'un nombre

function carre(x) {

  // TODO : compléter le code de la fonction

}


console.log(carre(0)); // Doit afficher 0

console.log(carre(2)); // Doit afficher 4

console.log(carre(5)); // Doit afficher 25

Modifiez ensuite le programme pour afficher le carré de tous les nombres entre 0 et 10. 

Pas question d'écrire bêtement dix appels àcarre() alors que vous savez maintenant comment répéter des instructions !
Minimum de deux nombres (résultat à obtenir)

Complétez le programmeminimum.js ci-dessous pour que la fonctionmin() renvoie le plus petit des deux nombres passés en paramètres.

// TODO : écrire la fonction min()


console.log(min(4.5, 5)); // Doit afficher 4.5

console.log(min(19, 9)); // Doit afficher 9

console.log(min(1, 1)); // Doit afficher 1

Calculatrice (résultat à obtenir)

Complétez le programmecalculatrice.js ci-dessous pour que la fonctioncalculer() gère les 4 opérations mathématiques de base : addition, soustraction, multiplication et division.

// TODO : écrire la fonction calculer()


console.log(calculer(4, "+", 6)); // Doit afficher 10

console.log(calculer(4, "-", 6)); // Doit afficher -2

console.log(calculer(2, "*", 0)); // Doit afficher 0

console.log(calculer(12, "/", 0)); // Doit afficher Infinity

Périmètre et aire d'un cercle (résultat à obtenir)

Ecrivez un programmecercle.js qui contient deux fonctionsperimetre() etaire() qui calculent respectivement le périmètre et l'aire d'un cercle à partir de son rayon. Testez vos fonctions avec un rayon saisi par l'utilisateur. 

Vous (re)trouverez les formules de calcul du périmètre et de l'aire d'un cercle en cherchant dans vos souvenirs... Ou bien sur Internet .

La valeur du nombre π (Pi) peut s'obtenir en JavaScript en écrivantMath.PI.
Solutions des exercices

Le code source des solutions est consultable en ligne. 

N'allez pas voir les solutions avant d'avoir bien cherché les exercices par vous-même !

Que pensez-vous de ce cours ?

    #

Activité : Créez un mini-jeu de devinette Manipulez les chaînes de caractères
Évoluez vers des programmes plus complexes

    Modularisez votre code grâce aux fonctions
    Manipulez les chaînes de caractères
    Créez vos premiers objets
    Trop classe, la POO !
    Stockez vos données dans des tableaux
    Conclusion et perspectives

    Quiz : Quiz 2
    Activité : Ecrivez un gestionnaire de contacts

Accéder au forum
Avec le soutien de
logo 3W Academy

Découvrir la formation développeur en 3 mois, HTML, CSS, Php, MySQL, Javascript.
Modifier le cours

    En cours de rédaction
    Publié

Modifier le cours

L'auteur
Baptiste Pesquet

Ingénieur et professeur agrégé, j'enseigne l'informatique et ses applications à l'Ecole Nationale Supérieure de Cognitique.
Découvrez aussi ce cours en...

    Premium
    Vidéo

OpenClassrooms

    Qui sommes-nous ?
    Fonctionnement de nos cours
    Recrutement
    Nous contacter

Professionnels

    Affiliation
    Entreprises
    Universités et écoles

En plus

    Créer un cours
    CourseLab
    Conditions Générales d'Utilisation

Suivez-nous

    Le blog OpenClassrooms

    English Español 

