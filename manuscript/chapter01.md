# 3, 2, 1... Codez !

Vous voici prêt(e) à passer aux choses sérieuses. Ce chapitre va vous faire découvrir les fondamentaux de la programmation : les notions de valeur et de type, ainsi que la structure générale d'un programme.

Tous les exemples de code du cours, ainsi que les solutions des exercices, sont disponibles en ligne. Vous pouvez consulter ce code avec un navigateur, ou le télécharger sous la forme d'une archive zip en suivant ce lien. Décompressez ensuite cette archive pour accéder à son contenu. 
Valeurs et types
Une valeur est un morceau d'information utilisé dans un programme informatique. Les valeurs existent sous différentes formes, appelées des types. Le type d'une valeur détermine son rôle et les opérations qui lui sont applicables. 

Chaque langage informatique dispose d'une panoplie de types qui lui est propre. Nous allons étudier deux des principaux types disponibles en JavaScript.

Le type nombre

Une valeur de type nombre (number) représente une valeur numérique, autrement dit une quantité. Comme en mathématiques, on distingue les valeurs entières (ou entiers) 0, 1, 2, 3... et les valeurs réelles (ou réels) auxquelles on ajoute des chiffres après la virgule pour plus de précision.

La virgule s'exprime en informatique sous la forme d'un point : 3.14 et non 3,14 !
Les nombres servent essentiellement à compter. Nous pouvons appliquer à des valeurs de type nombre les mêmes opérations qu'en mathématiques. Ces opérations produisent un résultat lui aussi de type nombre. Les principales opérations applicables sont rassemblées dans le tableau suivant.

Opérateur
Rôle
+
Addition
-
Soustraction
*
Multiplication
/
Division
La console des navigateurs Web modernes permet de taper du code JavaScript et d'observer le résultat de son exécution. Dans la console de Firefox, utilisez l'invite de commandes (le >> suivi d'un curseur clignotant) pour taper l'opération 8 * 4, puis appuyez sur Entrée. Vous obtenez le résultat attendu : 32. Testez ensuite d'autres opérations.


On remarque au passage qu'une division par zéro produit, comme attendu, un résultat infini (Infinity).
Le type chaîne

Une valeur de type chaîne de caractères (en abrégé chaîne, ou encore string en anglais) représente un texte. Ces valeurs sont délimitées par une paire de guillemets doubles : "Ceci est une chaîne".

Il est également possible de délimiter une chaîne de caractères avec une paire de guillemets simples : 'Ceci est aussi une chaîne'. Les avis divergent au sujet de la syntaxe à privilégier. Par convention, nous emploierons les guillemets doubles dans ce cours. L'important est d'être cohérent : utilisez l'une ou l'autre notation, mais ne mélangez pas les deux.
Il ne faut surtout pas oublier de "fermer" une chaîne : simples ou doubles, les guillemets vont toujours par deux !
Pour inclure dans une chaîne certains caractères spéciaux, on utilise le caractère \ (qui se prononce "antislash" ou "backslash" en anglais) qui donne un sens particulier au caractère suivant. Par exemple, \n permet d'ajouter un retour à la ligne dans une chaîne.

Dans la console du navigateur, entrez la ligne "Ceci est une chaîne \nSur plusieurs lignes" (en incluant les guillemets). Vous obtenez un résultat sur deux lignes.



On ne peut pas additionner ou supprimer des valeurs de type chaîne comme on peut le faire avec des nombres. En revanche, l'opérateur + peut être appliqué à deux valeurs de type chaîne. Son résultat est la jointure de ces deux chaînes, appelée concaténation.

Dans la console du navigateur, entrez la ligne "Bon"+"jour". Vous obtenez le résultat "Bonjour".



Affichage d'une valeur

Jusqu'à présent, nous avons utilisé la console du navigateur Web pour afficher des valeurs, mais nous n'avons pas véritablement programmé. Lorsqu'on souhaite afficher une valeur depuis un programme JavaScript, on utilise l'ordre JavaScript console.log(). La valeur à afficher est placée entre parenthèses et suivie d'un point-virgule. Il peut s'agir indifféremment d'un nombre ou d'une chaîne de caractères.

Nous pouvons maintenant expliquer le résultat du programme cours.js créé au chapitre précédent : il affiche la valeur "Bonjour en JavaScript", qui est de type chaîne.

console.log("Bonjour en JavaScript !");
Afficher un texte à l'écran (le fameux Hello World) est souvent la première chose que l'on apprend à faire lorsqu'on découvre un nouveau langage. Vous venez de franchir cette première étape !

Structure d'un programme
Nous avons précédemment défini un programme informatique comme étant une liste d'ordres indiquant à un ordinateur ce qu'il doit faire. Ces ordres sont écrits sous forme de texte dans un ou plusieurs fichiers et forment ce qu'on appelle le code source du programme. Les lignes de texte dans un fichier de code source s'appellent des lignes de code. 

Le code source peut comporter des lignes vides : celles-ci seront ignorées lors de l'exécution du programme.
Instructions

Chaque ordre inclus dans un programme est appelée une instruction. Une instruction est délimitée par un point virgule. Un programme est constitué d'une suite d'instructions. 

Le plus souvent, on n'écrit qu'une seule instruction par ligne, mais ce n'est pas une obligation.
Déroulement de l'exécution

Lorsqu'un programme est exécuté, les instructions qui le composent sont "lues" les unes après les autres. Chaque instruction produit un résultat, et c'est la combinaison de ces résultats individuels qui produit le résultat final du programme.

Nous pouvons observer ce comportement en exploitant une fonctionnalité extrêmement précieuse des navigateurs Web modernes comme Firefox : la possibilité de voir de l'intérieur ce qui se passe pendant l'exécution d'un programme JavaScript. Cette fonctionnalité est appelée débogage, car elle permet souvent de découvrir des bogues (bugs), c'est-à-dire des erreurs dans le code source du programme qui entraînent des dysfonctionnements pendant son exécution.

Avec Brackets, modifiez le programme cours.js afin de lui donner le contenu ci-dessous. 

console.log("Bonjour en JavaScript !");
console.log("Faisons quelques calculs.");
console.log(4 + 7);
console.log(12 / 0);
console.log("Au revoir !");
Ensuite, regardez la vidéo ci-dessous pour découvrir comment déboguer ce programme JavaScript avec Firefox.


 Télécharger la vidéo
Le débogage se base sur l'ajout de points d'arrêt (breakpoints). Comme son nom l'indique, un point d'arrêt permet de stopper l'exécution du programme à un endroit précis. L'exécution suivante du programme est bloquée au niveau du notre point d'arrêt. La ligne correspondante du code source est affichée en surbrillance. Ensuite, il est possible d'avancer étape par étape dans l'exécution (on parle d'exécution pas à pas) en observant le résultat produit par chaque instruction.

Commentaires

Par défaut, chaque ligne de texte dans les fichiers source d'un programme est considérée comme une instruction à exécuter. Il est possible d'exclure certaines lignes de l'exécution en les préfixant par une double barre oblique //. Ce faisant, on transforme ces lignes en commentaires.

Modifiez le programme cours.js en ajoutant // au début des lignes 2 et 4.

console.log("Bonjour en JavaScript !");
//console.log("Faisons quelques calculs.");
console.log(4 + 7);
//console.log(12 / 0);
console.log("Au revoir !");
Ouvrez ou rechargez le fichier cours.html dans Firefox : les lignes commentées ne produisent plus de résultat. En déboguant le programme, on peut vérifier que ces lignes ne sont plus exécutées.



Les commentaires servent à donner des informations sur le programme et sont destinées au programmeur, non à la machine.

Il existe une autre manière de créer des commentaires en entourant une ou plusieurs lignes par les caractères /* et */.
/* Un commentaire 
sur plusieurs
lignes */
 
// Un commentaire sur une seule ligne
Les commentaires fournissent une aide précieuse pour comprendre le code source d'un programme. Il est important de décrire les parties importantes ou compliquées d'un programme grâce à des commentaires. Prenez cette bonne habitude dès maintenant !
A vous de jouer !
Passons maintenant à quelques exercices pratiques pour vérifier que vous avez tout compris ! 

Pour chaque exercice, créez un fichier JavaScript dans le répertoire chapitre_1/js ainsi qu'un fichier HTML dans le répertoire chapitre_1/html. Le fichier HTML doit pointer vers le fichier JavaScript associé. Voici par exemple le contenu à donner au fichier presentation.html qui permet de tester le premier exercice.

<!doctype html>
<html>

<head>
    <meta charset="utf-8">
    <title>Présentation</title>
</head>

<body>
    <script src="../js/presentation.js"></script>
</body>

</html>
Si vous éprouvez des difficultés à réaliser les exercices, n'hésitez pas à étudier de nouveau le cours et à déboguer votre code.
Présentation (résultat à obtenir)

Ecrivez un programme presentation.js qui affiche votre nom et votre âge. Voici le résultat de l'exécution de ma version de ce programme.



Mini-calculatrice (résultat à obtenir)

Ecrivez un programme calculette.js qui calcule et affiche le résultat de l'addition, de la soustraction, de la multiplication et de la division de 6 par 3.

Valeurs affichées

Observez le programme valeurs.js ci-dessous puis tentez de prévoir les valeurs affichées lors de son exécution.

/*
Exercice : prévoir les valeurs affichées par ce programme
*/

console.log(4 + 5);
console.log("4 + 5");
console.log("4" + "5");
Vérifiez vos prévisions en créant ce programme puis en l'exécutant.