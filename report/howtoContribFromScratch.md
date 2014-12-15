How to contribute to Latexila ?
===============================

This document is designed for the begginers who want to start to contribute to a Gnome software. Latexila will be taken as an example, but this document can help for many other software from the **Gnome Project**.

Why this document ?
-------------------

We are a small team (3 people) at INSA Rennes, a french engineering school, who appened to work on Latexila.
We were not satisfied with the current documentation provided by the Gnome project, which is well documented but provide no real gothrought.

Goal
----
The goal of this document is to provide a walkthrought as complete as possible of the setup of a Latexila devlopper environement.

We choose Fedora as a starting point because it's the Linux distribution providing the broader support for the Gnome environement.

> The setup (download + first build) take something like 2h, but it's largely waiting time.

Resources
----------

[The Gnome project website for devloppers](https://developer.gnome.org/)
[Latexila's page](https://wiki.gnome.org/Apps/LaTeXila)
[Jhbuild HOWTO](https://wiki.gnome.org/HowDoI/Jhbuild)

Prerequired
-----------

### Computer
We assume that you have at you disposal a fresh or not-so-broken install of Fedora (21 preferred), and a resonable disk remaining (more than 10GB).
We assume you have administrator's priviledges.

> The testing was done on a fresh VM under Fedora-21-5-i686 (32bit)

### Human
We assume that you are not affraid of the command line.
You can copy/paste in most terminals using 'Ctrl'+'Shift'+'C' and 'Ctrl'+'Shift'+'V'.


The basics
----------

1. Install needed packets (hand picked)
	```BASH
	sudo yum install git gcc g++ gnome-common gtk3-devel vala gcc-c++ xorg-x11-util-macros mesa-libwayland-egl gtkspell3-devel intltool gtksourceview-devel gobject-introspection-devel lcov
	```
	Or even if you don't care... #brutforce
	```BASH
	sudo yum groupinstall development-libs development-tools gnome-software-development 
	```

2. Clone Latexila's repository (not required)
	```BASH
	git clone git://git.gnome.org/latexila
	```

Install Jhbuild
---------------

Inspired from [Jhbuild HOWTO](https://wiki.gnome.org/HowDoI/Jhbuild).

1. Creat a jhbuid directory where you want
```BASH
	mkdir ~/jhbuild
	cd ~/jhbuild
```

2. Make a shadow clone of the repo
```BASH
	git clone --depth=1 git://git.gnome.org/jhbuild
```

3. Install it _no root needed_
```BASH
	./autogen.sh --simple-install
 	make
 	make install
```

Now you can call jhbuil from the command line !

Install latexila using jhbuild
------------------------------

1. Get a config file sample at [swilmet's page](https://people.gnome.org/~swilmet/jhbuildrc-latexila).
2. Put it in ```/home/<user>/.config/jhbuildrc```
3. Either change the prefix ```/opt/gnome``` or make sure of the ```/opt``` access right.

> If you don't edit your config, the repositories will be put at ```/home/<user>/<repo>```

4. Get all the dependencies from the git repositories.
This can take a very~ long~ time~ if you have a laptop and a not-so-good internet conection.

> Average time is half an hour on a desktop with fiber

```BASH
	jhbuild update jhbuild
	jhbuild update latexila
```

> If you have an error, just use the choice you are given.
> At _hicolor-icon-theme_ for example, use choice ```1. Retry checkout```

Build Latexila
--------------

1. Install system dependencies
```BASH
	jhbuild sysdep --install
```
> Jhbuild will ask for root access during the process

2. Building vala
```BASH
	jhbuild update vala
	jhbuild build vala
```

3. Building the software
```BASH
	jhbuild build latexila
```
> The first build can take up to an hour or even two, depending on your workstation.
> Take a coffe and enjoy the run !

Run Latexila
------------

Juste type:
```BASH 
	jhbuild run latexila
```

> You can have a _distribution_ version of latexila by running the usual ```sudo yum install latexila```