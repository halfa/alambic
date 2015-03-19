TODO
====

## 1st step (done)

### Goal
Provide completion for “\ref” command using the labels defined in the current document.

### Recap
To do so, we are using the current structure of the _CompletionProvider_.
The major problem is that the update is done when the user saves the current file or when he clicks a button.
The fact is when the user is switching tab, there is no update from the provider. It means that between the moment
the user switch tab and the moment he saves, if he tries to use completion for a ```\ref``` he will have the proposals 
for the last file he was working on.

## 2nd step

Improve the current “\ref” completion by adding another structure to the CommpletionProvider class.
It implies to deal integrate our completion mechanism at a lower level of the program.
