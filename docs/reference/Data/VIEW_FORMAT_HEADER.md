##### Data Type : Views
##### VIEW_FORMAT_HEADER - Header structure used in VIEW_TABLE_FORMAT
---
```
#include <viewfmt.h>
```
**Description :**

This defines the structure of the header member of the VIEW_TABLE_FORMAT 
structure.  The VIEW_TABLE_FORMAT structure is part of a $VIEWFORMAT item (also 
known as a "View Table Format" item), which is an item in all view notes.

**Sample Usage :**
```

    VIEW_TABLE_FORMAT  ViewTableFormat;

/*
 * Initialize the VIEW_TABLE_FORMAT structure.
 */

    ViewTableFormat.Header.Version = VIEW_FORMAT_VERSION;
    ViewTableFormat.Header.ViewStyle = VIEW_STYLE_TABLE;
```
**See Also :**
[VIEW_TABLE_FORMAT](/reference/Data/VIEW_TABLE_FORMAT)
---
