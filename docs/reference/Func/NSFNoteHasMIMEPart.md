##### Function : MIME
##### NSFNoteHasMIMEPart - Check to see if the given note has any items of TYPE_MIME_PART
---
```
#include <nsfnote.h>
BOOL LNPUBLIC NSFNoteHasMIMEPart(

	NOTEHANDLE  hNote);
```
**Description :**

The function NSFNoteHasMIMEPart returns TRUE if the given note contains any 
TYPE_MIME_PART items.

**Parameters :**
Input :
hNote  -  a handle to an open note.

Output :
(routine)  -  TRUE if the given note has any TYPE_MIME_PART items, FALSE otherwise.



**Sample Usage :**
```
    BOOL bHasMIMEPart;


bHasMIMEPart = NSFNoteHasMIMEPart(hNote);

```
**See Also :**
[NSFNoteHasComposite](/reference/Func/NSFNoteHasComposite)
[NSFNoteHasMIME](/reference/Func/NSFNoteHasMIME)
[NSFNoteHasObjects](/reference/Func/NSFNoteHasObjects)
[NSFNoteHasRFC822Text](/reference/Func/NSFNoteHasRFC822Text)
---
