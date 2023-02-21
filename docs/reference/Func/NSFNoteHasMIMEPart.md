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
[NSFNoteHasComposite](/domino-c-api-docs/reference/Func/NSFNoteHasComposite)
[NSFNoteHasMIME](/domino-c-api-docs/reference/Func/NSFNoteHasMIME)
[NSFNoteHasObjects](/domino-c-api-docs/reference/Func/NSFNoteHasObjects)
[NSFNoteHasRFC822Text](/domino-c-api-docs/reference/Func/NSFNoteHasRFC822Text)
---
