##### Function : MIME
##### NSFNoteHasMIMEPart - Check to see if the given note has any items of TYPE_MIME_PART
---
##### #include <nsfnote.h>
BOOL LNPUBLIC **NSFNoteHasMIMEPart(**

	NOTEHANDLE  hNote);
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
[NSFNoteHasComposite](D:/md_files/NSFNoteHasComposite.md)
[NSFNoteHasMIME](D:/md_files/NSFNoteHasMIME.md)
[NSFNoteHasObjects](D:/md_files/NSFNoteHasObjects.md)
[NSFNoteHasRFC822Text](D:/md_files/NSFNoteHasRFC822Text.md)
---
