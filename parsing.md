#Where the method "parse" from DocumentStructure is called

```VALA
public DocumentStructure get_structure ()
{
	if (_structure == null)
        {
            _structure = new DocumentStructure (this);
            _structure.parse ();
        }
        return _structure;
	}
```

There is a parser for projects.

