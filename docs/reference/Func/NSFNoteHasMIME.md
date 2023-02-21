##### Function : MIME
##### NSFNoteHasMIME - Check to see if a note has any MIME content.
---
```
#include <nsfnote.h>
BOOL LNPUBLIC NSFNoteHasMIME(

	NOTEHANDLE  hNote);
```
**Description :**

The function NSFNoteHasMIME returns TRUE if the given note contains either 
TYPE_RFC822_TEXT items or TYPE_MIME_PART items.

**Parameters :**
Input :
hNote  -  a handle to an open note.

Output :
(routine)  -  TRUE if the given note has any MIME content, FALSE otherwise.



**Sample Usage :**
```
    BOOL bHasMIME;


bHasMIME = NSFNoteHasMIME(hNote);

```
**See Also :**
[NSFNoteHasComposite](/domino-c-api-docs/reference/Func/NSFNoteHasComposite)
[NSFNoteHasMIMEPart](/domino-c-api-docs/reference/Func/NSFNoteHasMIMEPart)
[NSFNoteHasObjects](/domino-c-api-docs/reference/Func/NSFNoteHasObjects)
[NSFNoteHasRFC822Text](/domino-c-api-docs/reference/Func/NSFNoteHasRFC822Text)
---
