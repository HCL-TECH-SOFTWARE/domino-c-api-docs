##### Function : NSFIsFileItemMimePart
##### NSFIsFileItemMimePart - Check to see given item ($File) has MIME part content. 
---
```
#include <nsfmime.h>
BOOL NSFIsFileItemMimePart(

	NOTEHANDLE  hNote,
	BLOCKID  bhMIMEItem);
```
**Description :**

Searches all TYPE_MIME_PART items on the note to see if the given $File item 
contains MIME part data. If $File item has MIME part, it returns TRUE. 
Otherwise, it returns FALSE.


**Parameters :**
Input :
hNote  -  Handle to the containing note.

bhMIMEItem  -  BLOCKID of the $File item to check.             

Output :
(routine)  -  TRUE, if the MIME part's content is in $File item. FALSE otherwise.



**Sample Usage :**
```
BLOCKID bhPart = { NULL }; 
STATUS error = NOERROR;
 NOTEHANDLE hNote = NULLHANDLE; /* Open Note handle */
 /* Get BLOCKID of note item into bhPart */ 
if (NSFIsFileItemMimePart(hNote, bhPart))
{
printf("\nMIME part content is in $File item.\n");
}
```
**See Also :**
---
