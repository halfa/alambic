First approache of the code
=======================

Let's see what we can do !

Directories
----------------
Here are the directories, with comments:

	data/ 	icons, images and templates used by latexila
	docs/ 	reference manual
	help/	reference files (and some translations?)
	m4/		macro for valac
	man/	manpage
	po/		language files for latexila
	src/	code in vala !
	tests/	code coverage and test tools
	vapi/	?

Main
--------

Use of two ```main```:

- one for command line call
- one for app call 


Interesting files/methods
-----------------------

- document -> parser
- document_structure -> variables and structures to describe a document
	- get_markup_type
	- search_markup
	- get_markup_content
	- handle_item
	
- completion -> ```CompletionProvider```
