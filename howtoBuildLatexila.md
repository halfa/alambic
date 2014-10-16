HowTo build latexila
=================

*A hopefully short but deseperatly long todo-list*

Edited in **Markdown**, following [GitHub](https://help.github.com/articles/markdown-basics/)
syntax.

The downloadseption
---------------------------------

### I want data

1. install git
2. use it to clone gnome's latexila repo with

        git clone git://git.gnome.org/latexila
3. now the tools : ```git clone git://git.gnome.org/gnome-common```
4. activate the source repo in source.list and refresh packet manager 
5. install some packages(1) :

#### Ubuntu 14.10/Debian-testing
    sudo apt-get build-dep latexila
get sources requirements, then
 
    sudo apt-get install gtk-doc-tools gnome-devel gobject-introspection
(that's _super_ heavy !)

**Ubuntu** PPA for **valac** v0.25.4

    sudo add-apt-repository ppa:vala-team

Optional ?  ```sudo apt-get install gnome-core-devel gnome-platform-devel```

#### Fedora 20
Install latexila's dependencies

    yum-builddep latexila

##### References
- [APT - Build dependencies of a package](http://askubuntu.com/questions/21379/how-do-i-find-the-build-dependencies-of-a-package)
- [vala-team/ppa](https://launchpad.net/~vala-team/+archive/ubuntu/ppa)
- [jhbuild for dependencies](https://wiki.gnome.org/Projects/Jhbuild/Dependencies/Fedora)

Install it
------------
### Gimme code
_Maybe this step can be skipped with appropriate packages ?_

1. Configure *gnome-commons* by using ``` ./autogen.sh ```
2. Build and install ```sudo make install```

For later - Setup a working dev-env
-------------------------------------

1. Install vim
2. Learn to use vim
3. Install vim-airline
4. Install vim-fugitive
5. Install vala.vim
6. Learn how to use git
7. ...
