##### Function : ID Table
##### IDTableSetFlags - Sets the Flag information of an ID Table.
---
##### #include <idtable.h>
void LNPUBLIC **IDTableSetFlags(**

	void far *pIDTable,
	WORD  Flags);
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
[IDTableFlags](D:/md_files/IDTableFlags.md)
[IDTableSetTime](D:/md_files/IDTableSetTime.md)
[IDTableSize](D:/md_files/IDTableSize.md)
[IDTableTime](D:/md_files/IDTableTime.md)
[IDTABLE_xxx](D:/md_files/IDTABLE_xxx.md)
---
