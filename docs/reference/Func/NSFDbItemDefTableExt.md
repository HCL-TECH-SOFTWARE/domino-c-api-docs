##### Function : Database
##### NSFDbItemDefTableExt - Get the extended version of the database's Item Definition Table.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbItemDefTableExt(

	DBHANDLE  hDB,
	ITEMDEFTABLEEXTHANDLE far *retItemNameTable);
```
**Description :**

The extended version of the Item Definition Table for a database contains the 
number of items, name and type of all the items defined in that database.  
Examples are field names, form names, design names, and formula labels.  
Applications can obtain a copy of the extended version of the Item Definition 
Table by calling NSFDbItemDefTableExt, which returns a memory handle for the 
copy of the table.  The application can then call the following functions to 
lock, extract, unlock, and free information from the table:

        NSFItemDefExtLock, NSFItemDefExtEntries, NSFItemExtGetEntry, 
NSFItemDefExtUnlock, NSFItemDefExtFree.

For details on the structure of the extended version of the Item Definition 
Table, please see the descriptions for ITEM_DEFINITION_TABLE_EXT,  
ITEM_DEFINITION_EXT, and ITEM_DEFINITION_TABLE_LOCK.


**Parameters :**
Input :
hDB  -  A handle to the Domino database.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Operation succeeded.



retItemNameTable  -  The address of an ITEMDEFTABLEEXTHANDLE where the handle for the extended version of the Item Definition Table of a database is returned.


**Sample Usage :**
```
    /* Local data declarations */
    
    /* database handle */
    DBHANDLE                                    db_handle;
    ITEMDEFTABLEEXTHANDLE                       hItemDefExt;
    ITEM_DEFINITION_TABLE_EXT                   *pItemDefExt;
    ITEM_DEFINITION_TABLE_LOCK                  ExtLock;
    DWORD                                       i, NumEntries;
    WORD                                        ItemType, ItemLength;
    char                                        *pItemName;
    char                                        ItemName[128];
    char                                        NewItemName[128];
    char                                        *db_name;
    char                                        szDBName[MAXPATH];
    STATUS                                      error=0;
 
    db_name = szDBName;
    
    /* Open the database. */
    
    if (error = NSFDbOpen (db_name, &db_handle))
	goto Exit0;
    
    /* Get a handle to the ITEM_DEFINITION_TABLE_EXT structure */
    
    if (error = NSFDbItemDefTableExt (db_handle, &hItemDefExt))
	goto Exit1;

    /* lock the ITEM_DEFINTION_TABLE_EXT structure and get a pointer */

    pItemDefExt = OSLock(ITEM_DEFINITION_TABLE_EXT, hItemDefExt);

    /* Lock the contents of the ITEM_DEFINITION_EXT structure */
    
    if (error = NSFItemDefExtLock(pItemDefExt, &ExtLock))
	goto Exit2;

    /* Get the number of item entries from the structure */
    
    if (error = NSFItemDefExtEntries(&ExtLock, &NumEntries))
	goto Exit3;

    printf("NumEntries:%d\n\n",NumEntries);
    
    pItemName = &ItemName[0];

    /* for each item... */
    for (i=0; i<NumEntries; i++)
    {

      /* get the item's type, length, and name */
      if (error = NSFItemDefExtGetEntry(&ExtLock, i, &ItemType, &ItemLength, 
&pItemName))
	  goto Exit3;

      /* copy character stream up to Item Length */
      memcpy(&NewItemName[0],pItemName,ItemLength);
	  
      /* null terminate the character stream */
      NewItemName[ItemLength]='\0';
      
      printf("Item %d\n", i);
      printf("ItemType:%d\n", ItemType);
      printf("ItemLength:%d\n", ItemLength);
      printf("ItemName:%s\n\n", NewItemName);
    }

Exit3:

    /* Unlock the ITEM_DEFINITION_EXT structure within the 
ITEM_DEFINITION_TABLE_EXT
       structure */
    
    if (!error)
      error = NSFItemDefExtUnlock(pItemDefExt, &ExtLock);

Exit2:

    /* Free the contents of the ITEM_DEFINITION_EXT structure within the 
       ITEM_DEFINITION_TABLE_EXT */
    if (!error)
      error = NSFItemDefExtFree(pItemDefExt);

    /* unlock and free the handle to the ITEM_DEFINITION_TABLE_EXT structure */
    OSUnlock(hItemDefExt);
    OSMemFree(hItemDefExt);



Exit1:
    /* Close the database. */
    
    NSFDbClose (db_handle);

Exit0:

    return(ERR(error));

}

```
**See Also :**
[ITEM_DEFINITION_EXT](/reference/Data/ITEM_DEFINITION_EXT)
[ITEM_DEFINITION_TABLE_EXT](/reference/Data/ITEM_DEFINITION_TABLE_EXT)
[ITEM_DEFINITION_TABLE_LOCK](/reference/Data/ITEM_DEFINITION_TABLE_LOCK)
[NSFItemDefExtEntries](/reference/Func/NSFItemDefExtEntries)
[NSFItemDefExtFree](/reference/Func/NSFItemDefExtFree)
[NSFItemDefExtGetEntry](/reference/Func/NSFItemDefExtGetEntry)
[NSFItemDefExtLock](/reference/Func/NSFItemDefExtLock)
[NSFItemDefExtUnlock](/reference/Func/NSFItemDefExtUnlock)
---
