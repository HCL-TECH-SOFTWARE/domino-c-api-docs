##### Symbolic Value : Note
##### IDTABLE_xxx - IDTable - Flags
---
##### #include <idtable.h>
**Description :**
These defines are used in conjunction with IDTableFlags and IDTableSetFlags.
**Sample Usage :**
```
  
 
   if (IDTableFlags(idtable_ptr) & IDTABLE_MODIFIED)
       /* Well we didn't,so NSFDbGetModifiedNoteTable() must have */
       /* Will clear modified flag for our own puposes            */
       IDTableSetFlags(idtable_ptr, 0);

```
**See Also :**
[IDTableFlags](D:/md_files/IDTableFlags.md)
[IDTableSetFlags](D:/md_files/IDTableSetFlags.md)
---
