##### Symbolic Value : OLE
##### NOTES_OLE_PRINT_VERB_USA - U. S. English print verb
---
```
#include <olenotes.h>
```

**Symbolic Values :**



**Description :**

If you want your OLE object to receive the NOTES_DOC_INFO_MSG message when the document containing your objects is printed, then your application must handle an OleActivate() using the predefined printing verb named &quot;Print&quot; (for USA), or translated to the localized country translation, which matches that of the translation used by Domino and Notes.  Domino and Notes actually store the localized string &quot;Print&quot; in its string resources, and does not actually use this constant in compiled code.  However, it is defined as a convenience to Domino and Notes C API developers as a reference.


**See Also :**
---
