# Guide de style

Voici les règles de codage utilisées dans ce livre.

## Nommage

Bien nommer les choses permet de rendre les programmes plus faciles à comprendre et à modifier. Voici quelques règles générales à ce sujet.

### Choisir des noms significatifs

La règle la plus importante est de donner à tout élément cu code (variable, fonction, classe, etc) un nom qui reflète son rôle. Une variable qui contient la valeur du rayon d'un cercle devrait être nommée `rayon` plutôt que `num` et `maValeur`.‌

Les noms très courts devraient être réservés aux éléments dont la portée est faible (compteur de boucle par exemple).

### Bannir les caractères accentués

Les caractères accentués comme `é` ou `à` sont mal supportés dans certains environnements et sont inconnus du monde anglophone. Mieux vaut les éviter : on nommera une variable `perimetre` plutôt que `périmètre`.

### Ne pas utiliser les noms réservés du langage

Les mots-clés du langage JavaScript sont des noms réservés. Ils ne doivent pas être utilisés comme noms de variables. Vous trouverez sur [cette page](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Mots_r%C3%A9serv%C3%A9s) la liste des noms réservés de JavaScript.

### Adopter une convention de nommage

Il faut parfois plusieurs mots pour décrire le rôle de certaines variables. Dans ce cas, on a intérêt à adopter une **convention de nommage**, c'est-à-dire une manière uniforme d'écrire les noms de toutes les variables. Il en existe plusieurs. Dans ce cours, nous allons adopter la plus fréquemment utilisée : la norme [camelCase](https://fr.wikipedia.org/wiki/CamelCase) (appelée parfois *lowerCamelCase*). Elle repose sur deux grands principes :

* Tout nom de variable commence par une **lettre minuscule**.
* Si le nom d'une variable se compose de plusieurs mots, la première lettre de chaque mot (sauf le premier) s'écrit en **majuscule**.

Par exemple, les noms `montantTravauxMaison` et `codeClientSuivant` respectent la norme *camelCase*.

W> Comme de nombreux langages, JavaScript fait la distinction entre majuscules et minuscules. On dit qu'il est **sensible à la casse** (*case sensitive*). Par exemple, `mavariable` et `maVariable` seront considérées comme deux variables différentes. Attention aux étourderies !

## Formatage du code

Il s'agit d'un sujet hautement subjectif et personnel, qui fait l'objet d'infinis débats : espaces ou tabluations, guillemets simples ou doubles, etc. Une solution simple et efficace consiste à utiliser un outil qui automatise le formatage. Le standard pour l'écosystème JavaScript est [Prettier](https://prettier.io/).

## Qualité du code

JavaScript étant un langage à typage dynamique, un certain nombre d'erreurs dans le code de vos programmes ne se révèleront qu'au moment de l'exécution, comme par exemple une erreur dans le nom d'une variable ou d'une fonction.

Pour limiter ces risques de défauts, vous pouvez utiliser un outil d'analyse du code (*linting*) comme [ESLint](http://eslint.org/). Il existe des configurations prédéfinies pour cet outil, comme par exemple le [guide de style JS d'AirBnb](https://github.com/airbnb/javascript) qui constitue une lecture recommandée.

Les exemples de code et les exercices de ce livre sont basés sur cette configuration, avec quelques variations mineures. Voici pour information la configuration exacte utilisée (elle est définie dans le fichier .eslintrc).

```json
{
  "extends": ["airbnb", "prettier"],
  "env": {
    "browser": true
  },
  "plugins": ["prettier"],
  "rules": {
    "no-console": "off",
    "no-alert": "off",
    "no-plusplus": "off",
    "default-case": "off",
    "no-param-reassign": [
      "error",
      {
        "props": false
      }
    ],
    "arrow-body-style": [
      "error",
      "as-needed",
      { "requireReturnForObjectLiteral": true }
    ]
  }
}
```
