##### Function : MIME
##### NSFNoteHasRFC822Text - Check to see if the given note has any items of TYPE_RFC822_TEXT.
---
```
#include <nsfnote.h>
BOOL LNPUBLIC NSFNoteHasRFC822Text(

	NOTEHANDLE  hNote);
```
**Description :**

The function NSFNoteHasRFC822Text returns TRUE if the given note contains any 
TYPE_RFC822_TEXT items.

**Parameters :**
Input :
hNote  -  a handle to an open note.

Output :
(routine)  -  TRUE if the given note has any TYPE_RFC822_TEXT items, FALSE otherwise.




**Sample Usage :**
```
    BOOL bHasRFC822Text;


bHasRFC822Text = NSFNoteHasRFC822Text(hNote);

```
**See Also :**
[NSFNoteHasComposite](/reference/Func/NSFNoteHasComposite)
[NSFNoteHasMIME](/reference/Func/NSFNoteHasMIME)
[NSFNoteHasMIMEPart](/reference/Func/NSFNoteHasMIMEPart)
[NSFNoteHasObjects](/reference/Func/NSFNoteHasObjects)
---
