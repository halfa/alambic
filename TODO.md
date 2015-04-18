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

## 2nd step (done)

### Goal
Provide completion for "\ref" using labels sourced from all opened documents

## 3rd step (done)

### Goal
Provide completion for "\ref" using labels sourced only from files of the same folder, parse the files in background

### Recap
Parser is detatched from document_structure and integrated into the document class itself.
Use of a global _Set_ to store data parsed, and sourced by the completion provider to build the label list provided.

## 4th step

### Goal
When a file is opened, look for projet main file, parse it and parse any following includes recursively.

### Recap
[...]
