##### Function : ID Table
##### IDTableSetFlags - Sets the Flag information of an ID Table.
---
```
#include <idtable.h>
void LNPUBLIC IDTableSetFlags(

	void far *pIDTable,
	WORD  Flags);
```
**Description :**

This function sets the Flag information of an ID Table.  See the IDTABLE_xxx 
symbols for further information.

**Parameters :**
Input :
pIDTable  -  A pointer to an ID Table.

Flags  -  A WORD containing the IDTABLE_xxx flags you'd like to have associated with the ID Table.

Output :
(routine)  -  None.



**Sample Usage :**
```

   if (IDTableFlags(idtable_ptr) & IDTABLE_MODIFIED)

       /* Well we didn't,so NSFDbGetModifiedNoteTable() must have */
       /* Will clear modified flag for our own puposes            */

       IDTableSetFlags(idtable_ptr, 0);

```
**See Also :**
[IDTableFlags](/domino-c-api-docs/reference/Func/IDTableFlags)
[IDTableSetTime](/domino-c-api-docs/reference/Func/IDTableSetTime)
[IDTableSize](/domino-c-api-docs/reference/Func/IDTableSize)
[IDTableTime](/domino-c-api-docs/reference/Func/IDTableTime)
[IDTABLE_xxx](/domino-c-api-docs/reference/Symb/IDTABLE_xxx)
---
