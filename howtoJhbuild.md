Jhbuild is awesome
==================

This is how Gnome describe Jhbuild:

> Jhbuild is the recommended way to build and run GNOME development code. It will download the code, 
> configure and build it for you, in a way that does not interfere with or modify your existing system

Installation
------------

Follow these instructions -> [Jhbuild](https://wiki.gnome.org/HowDoI/Jhbuild)
[Dependencies under Fedora](https://wiki.gnome.org/Projects/Jhbuild/Dependencies/Fedora)

Install a software for me please
--------------------------------

To install and build latexila and (quite) all his dependencies use :

    jhbuild build latexila

To run latexila :

    jhbuild run latexila

You may need others modules you can install with :

    jhbuild buildone *module*

Tips
----

If you got” *configure: error: vapigen not found*” you may install vala :

    jhbuild buildone vala


The Latexila source folder is located in *prefix_install*/jhbuild/checkout/latexila. Remember <code>ln -s </code>
