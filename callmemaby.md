# ```Parser()``` calls

What happens when a document is save (parsing POV)

### Methods

1. File: main_window.vala | Method: save_document(Document doc, bool force_save_as)
2. File: structure.vala | Method: public void refresh ()
3. File: structure.vala | Method: private void show_document (Document? doc, bool force_parse = false)

### Summary

When a document is saved (i.e. when the method 1 is called) and if thsi document is the active one, 
the doc structure is refresh via ```_main_window_structure.refresh ();``` (2)

The method called refresh (2)is a single call to the method 3 with the argument force_parse set at True. It 
fullfill the condition ```if (force_parse)``` and call the method ```_document_structure.parse ();```

That's all folks!