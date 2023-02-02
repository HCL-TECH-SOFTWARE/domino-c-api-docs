##### Function : ID Table
##### IDTableFlags - Returns a WORD containing the Flag settings for the specified ID Table.
---
##### #include <idtable.h>
WORD LNPUBLIC **IDTableFlags(**

	void far *pIDTable);
**Description :**
This function returns a WORD containing the Flag settings for the specified ID 
Table.  See IDTABLE_xxx symbols for the possible Flag settings.
**Parameters :**
Input :
pIDTable  -  A pointer to an ID Table.

Output :
(routine)  -  Returns the Flag settings for the specified ID Table.


**Sample Usage :**
```

   if (IDTableFlags(idtable_ptr) & IDTABLE_MODIFIED)
 
       /*  NSFDbGetModifiedNoteTable() set this flag.  */
       /* Clear the modified flag for our own puposes. */

       IDTableSetFlags(idtable_ptr, 0);

```
**See Also :**
[IDTableSetFlags](D:/md_files/IDTableSetFlags.md)
[IDTableSetTime](D:/md_files/IDTableSetTime.md)
[IDTableSize](D:/md_files/IDTableSize.md)
[IDTableTime](D:/md_files/IDTableTime.md)
---
