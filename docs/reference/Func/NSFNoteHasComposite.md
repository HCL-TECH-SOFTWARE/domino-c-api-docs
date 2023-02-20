##### Function : MIME
##### NSFNoteHasComposite - Check to see if the given note has any items of TYPE_COMPOSITE.
---
```
#include <nsfnote.h>
BOOL LNPUBLIC NSFNoteHasComposite(

	NOTEHANDLE  hNote);
```
**Description :**

The function NSFNoteHasComposite returns TRUE if the given note contains any 
TYPE_COMPOSITE items.

**Parameters :**
Input :
hNote  -  a handle to an open note.

Output :
(routine)  -  TRUE if the given note has any TYPE_COMPOSITE items, FALSE otherwise.



**Sample Usage :**
```
    BOOL bHasComposite;


bHasComposite = NSFNoteHasComposite(hNote);

```
**See Also :**
[NSFNoteHasMIME](/reference/Func/NSFNoteHasMIME)
[NSFNoteHasMIMEPart](/reference/Func/NSFNoteHasMIMEPart)
[NSFNoteHasObjects](/reference/Func/NSFNoteHasObjects)
[NSFNoteHasRFC822Text](/reference/Func/NSFNoteHasRFC822Text)
---
