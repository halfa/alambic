Comment contribuer à latexila
==========================

Ce document est conçu pour les débutants qui veulent commencer à contribuer à un logiciel Gnome. Latexila sera pris comme exemple, mais ce document peut aider pour beaucoup d'autres logiciels du projet Gnome, en particulier ceux qui utilisent `jhbuild`.

Pourquoi ce document?
-------------------

Nous sommes une petite équipe (3 étudiants) de l'INSA de Rennes, une école d'ingénieurs française, qui ont travaillé sur latexila.
Nous n'étions pas satisfaits de la documentation actuelle fournie par le projet Gnome, qui est bien documenté, mais ne fournit aucune réelle recette.

Objectif
----
Le but de ce document est de fournir un parcours aussi complet que possible de la configuration d'un environnement de développement pour Latexila.
Nous choisissons Fedora comme un point de départ car c'est la distribution Linux qui dispose du meilleur support pour l'environement Gnome.

> La configuration (téléchargement + première construction) prennent quelque chose comme 2h, mais il s'agit surtout de temps d'attente.

Ressources
----------

* [Le site du projet Gnome pour les dévloppeurs] (https://developer.gnome.org/)
* [La page de latexila sur GNOME.org] (https://wiki.gnome.org/Apps/LaTeXila)
* [JHBuild HOWTO] (https://wiki.gnome.org/HowDoI/Jhbuild)

Prérequis
-----------

### Computer
Nous supposons que vous avez à votre disposition une installation fraiche (ou presque) de Fedora (21 si possible), et un espace disque raisobable restant (plus de 10 Go). Nous supposons également que vous disposez des privilèges d'administrateur.

> Le test a été effectué sur une installation de Fedora 21 Workstation (64bit) mise à jour en date du 18 mars 2015
> La version de latexila était la dernière en date

### Être Humain
Nous supposons que vous n'avez pas peur de la ligne de commande.
Vous pouvez copier/coller des commandes dans la plupart des terminaux à l'aide 'Ctrl' 'Shift' + 'C' et 'Ctrl' + 'Shift' + 'V'.


Les bases
----------

1. Installez les paquets nécessaires
`` `BASH
sudo yum install git gcc gnome-commune gtk3-devel vala gcc-c ++ xorg-x11-util-macros mesa-libwayland-EGL intltool gtksourceview-devel-gobject introspection-devel lcov de gtkspell3-devel
`` `
Ou si vous pensez en avoir besoin...  #bruteforce
`` `BASH
sudo yum groupinstall développement-libs développement-outils gnome-développement logiciel
`` `

Installez JHBuild
---------------

Inspiré du [HOWTO JHBuild] (https://wiki.gnome.org/HowDoI/Jhbuild).

1. Faire un clone mono-niveau du dépôt
`` `BASH
git clone --depth = 1 git: //git.gnome.org/jhbuild
`` `
2. Installez le, _droits root non requis_
`` `BASH
./autogen.sh --simple installer
 make
 make install
`` `

Maintenant vous pouvez appeler `jhbuild` de la ligne de commande !

Installez latexila utilisant jhbuild
------------------------------

1. Obtenir un échantillon du fichier de configuration sur [la page de swilmet] (https://people.gnome.org/~swilmet/latexila/jhbuildrc).
2. Mettez-le dans `` `/ home / <utilisateur> /. Config / jhbuildrc```
3. Changez le préfixe du chemein pour quelque chose de différent ou assurez-vous des droits d'accès pour l'utilisateur actuel.
> Si vous ne modifiez pas votre configuration, les dépôts seront mis à `` `/ home / user <> / <repo>` `` et les fichiers seront compilés vers `` `/ opt```

4. Obtenez toutes les dépendances des dépôts git.
Cela peut prendre beaucoup de  temps si vous avez un ordinateur portable et une connexion internet très limité, car certains des dépôts sont gros, comme ` Glib` ou `GTK3`.

> Durée moyenne une demi-heure sur un ordinateur de bureau avec accès internet en fibre

`` `BASH
jhbuild update latexila
`` `
> Si vous avez une erreur, essayez les choix qui vous sont donnés, un par un et, si nécessaire, chercher les paquets nécessaires en utilisant `yum search`.

Construire latexila
--------------

1. Installez (ou vérifier) les dépendances du système
`` `BASH
jhbuild sysdeps --install
`` `
> JHBuild demandera un accès root au cours du processus

2. Compiler vala
`` `BASH
jhbuild update vala
jhbuild build  jhbuild
`` `

3. Compiler le logiciel et toutes ses dépendances
`` `BASH
jhbuild make latexila
`` `
> La première construction peut prendre jusqu'à une heure, voire deux, selon la puissance de votre machine.
> Allez prendre un café!

4. Compilation de Latexila uniquement
Si vous voulez compilier uiquement latexila, vous pouvez le faire en utilisant
`` `BASH
jhbuild buildone latexila
`` `
Cela va construire la version actuelle de `master`.

5. compiler la branche courante pour les tests
`` `BASH
# Dans [...] / latexila
jhbuild make
`` `

Exécuter latexila
------------

Exécuter
`` `BASH
jhbuild run latexila
`` `

> Vous pouvez disposer d'une version _distribution_ de latexila en exécutant l'habituel `` `sudo yum install latexila```