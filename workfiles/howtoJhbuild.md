Jhbuild is awesome
==================

This is how Gnome describes Jhbuild:

> Jhbuild is the recommended way to build and run GNOME development code. It will download the code, 
> configure and build it for you, in a way that does not interfere with or modify your existing system

Installation
------------

Follow these instructions -> [Jhbuild](https://wiki.gnome.org/HowDoI/Jhbuild) and you might need to intall this 
[dependencies under Fedora](https://wiki.gnome.org/Projects/Jhbuild/Dependencies/Fedora). Mind what you're doing.

When jhbuild is installed, copy the config file relative to your project in ~/.config/jhbuildrc.

Install a software for me please
--------------------------------

To install and build latexila and (quite) all his dependencies use :

    jhbuild build latexila
 
You may need other modules you can install with :

    jhbuild buildone *module*

Run a software
-----------------

To run latexila :

    jhbuild run latexila


Tips
----

If you got this : ”*configure: error: vapigen not found*”,  you have to install vala :

    jhbuild buildone vala


The Latexila source folder is located in **prefix_install**/jhbuild/checkout/latexila. Remember ```ln -s ```.
