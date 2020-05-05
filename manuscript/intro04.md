# Environnement de travail

Le pré-requis essentiel pour suivre ce livre est d'utiliser un [navigateur web](https://fr.wikipedia.org/wiki/Navigateur_web) récent. Plus précisément, votre navigateur doit être capable d'exécuter du code JavaScript conforme à la spécification ES2015 du langage JavaScript. C'est le cas de Firefox, Chrome, Safari ou encore Microsoft Edge. A l'inverse, évitez d'utiliser Internet Explorer qui est maintenant obsolète.

## Solution 1 : coder en ligne

Si vous êtes du genre impatient et/ou que vous ne pouvez pas installer de logiciels sur votre machine, vous pouvez coder en ligne grâce à l'un des nombreux bacs à sable (*playgrounds*) JavaScript existants. [CodePen](https://codepen.io) est un bon choix, de même que [JS Fiddle](https://jsfiddle.net/) et [JS Bin](http://jsbin.com/). Si vous utilisez CodePen, visitez [ce lien](https://codepen.io/hello/) pour découvrir le fonctionnement de cette plate-forme.

## Solution 2 : installer un environnement local

Cette solution demande un peu plus de temps et de travail, mais vous permettra d'obtenir un environnement personnalisé et confortable. Avoir un environnement dédié deviendra de toute façon nécessaire lorsque vous vous attaquerez à des projets plus ambitieux.

Vous devez disposer sur votre machine des éléments suivants :

* Un éditeur de code. [Visual Studio Code](https://code.visualstudio.com/), [Atom](https://github.com/atom) ou encore [Sublime Text](https://www.sublimetext.com/) sont de bons choix.
* La plate-forme [Node.js](https://nodejs.org). Téléchargez une version récente (par exemple la dernière version LTS, *Long Time Support*) puis suivez les instructions d'installation.
* L'outil de formatage automatique du code [Prettier](https://prettier.io/), pas complètement obligatoire mais tellement pratique.

Une fois ces éléments installés, enregistrez vos programmes JavaScript dans le répertoire de votre choix, sous la forme de fichiers portant l'extension `.js` (par exemple : `chapitre1-1.js`). Ensuite, vous pourrez les exécuter en ouvrant une fenêtre de terminal, puis en lançant une commande de la forme :

```bash
node nomDuFichier.js
```

> Si vous n'avez jamais utilisé le terminal sur votre machine, consultez la première partir de [ce cours](https://openclassrooms.com/fr/courses/6173491-apprenez-a-utiliser-la-ligne-de-commande-dans-un-terminal?status=published) pour acquérir les bases.
