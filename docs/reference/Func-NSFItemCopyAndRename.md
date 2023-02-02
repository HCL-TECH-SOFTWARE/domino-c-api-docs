##### Function : Database
##### NSFItemCopyAndRename - Copy an item from one note to another note and rename it.
---
##### #include <nsfnote.h>
STATUS **NSFItemCopyAndRename(**

	DHANDLE  hnote,
	BLOCKID  bhItem,
	const char *pszNewItemName);
**Description :**
Copy a single item from one note to the end of another note. Optionally rename 
the item in the target note.
**Parameters :**
Input :
hnote  -  It is an open Note handle.

bhItem  -  The block id of the note item to be copied.

pszNewItemName  -  An optional new name for the destination item.  If NULL, name is copied with original item.

Output :
(routine)  -  Return status from the call either success or an error. 
              NOERROR, on success.


**Sample Usage :**
```
	/* Presumes hSrcNote and hDstNote are both opened NOTEHANDLES prior to 
calling. */

  void far PASCAL CopyItem(NOTEHANDLE hSrcNote,char *pSrcItem, NOTEHANDLE 
hDstNote,char *pDstItem)
  {
   BLOCKID bhItem;
   char *pEffectiveDstItem = (pDstItem ? pDstItem : pSrcItem);
	 char szDstItem[MAXINTF]; 

	 // To deal with both responses and the parent, shortcut a copy to 
self. 
	 // 
	 if (hSrcNote == hDstNote) 
	  return; 

	 NSFItemDelete(hDstNote, szDstItem, Cstrlen(szDstItem));
  
	 if (NOERROR == NSFItemInfo(hSrcNote, pSrcItem, Cstrlen(pSrcItem), 
&bhItem, NULL, NULL, NULL)) 
	 {
    BLOCKID bhNewItem; 

	  NSFItemCopyAndRename(hDstNote, bhItem, szDstItem);
 
	  if (NOERROR == NSFItemInfo(hDstNote, szDstItem, Cstrlen(szDstItem), 
&bhNewItem, NULL, NULL, NULL))
    {
     NOTE_ITEM *item = OSLockBlock(NOTE_ITEM,bhNewItem);
     item->ItemFlags |= ITEM_SUMMARY; 
	   OSUnlockBlock(bhNewItem); 
	  }
   }
  }
```
**See Also :**
[](D:/md_files/.md)
---
