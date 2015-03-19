# Prototypes from interesting methods

## In file document_structure.vala

Methods
```VALA
private StructType? get_markup_type (string markup_name)

private bool search_markup (string line, int after_backslash_index, out StructType? type, out string? contents, out int? end_match_index)
        
private string? get_markup_contents (string line, int begin_contents_index, out int? end_match_index)

private void handle_item (StructType type, string? contents, TextIter iter)

private bool search_low_level_item (string line, int start_index, out StructType? type, out string? contents, out int? start_match_index, out int? end_match_index)
```

Variables
```VALA
public bool parsing_done { get; private set; default = false; }
```


## In file structure_model.vala

```VALA
private Gee.ArrayList<unowned Node<StructData?>>? get_list (StructType type)

```
