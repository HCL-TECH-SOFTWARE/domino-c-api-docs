##### Function : Database
##### NSFDbStampNotes - Set same item value for every note in ID Table.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbStampNotes(**

	DBHANDLE  hDB,
	DHANDLE  hTable,
	const char far *ItemName,
	WORD  ItemNameLength,
	void far *Data,
	WORD  DataLength);
**Description :**
This function takes a given item value and stores it in all the notes specified 
by an ID Table.  It overwrites the current item value, thereby updating the 
last modified time/date of each Note processed.  If the item does not exist or 
is of a different data type, NSFDbStampNotes() will create/delete the item and 
append the new value as required.

If you do not have the proper access to modify any one of the notes in the ID 
Table, ERR_NOACCESS will be returned.  Only those documents you are able to 
modify have been stamped.
**Parameters :**
Input :
hDB  -  A handle to a Domino database.

hTable  -  A handle to an ID Table.

ItemName  -  A pointer to a string containing the name of the Item you wish to operate on.  This string does not have to be null-terminated.

ItemNameLength  -  A WORD containing the length of the Item name.

Data  -  A pointer to the value.  The first WORD of that storage must be the Domino data type, followed by the data itself.  If the API program is running on a non-Intel architecture system, and item type is one of TYPE_COMPOSITE, TYPE_COLLATION, TYPE_OBJECT, TYPE_VIEW_FORMAT, TYPE_ICON, TYPE_SIGNATURE, TYPE_SEAL, TYPE_SEALDATA, TYPE_SEAL_LIST, TYPE_WORKSHEET_DATA or TYPE_USERDATA, then the data pointed to by Data must be in Domino canonical format.

DataLength  -  A WORD containing the length of the data, including the leading WORD of data type.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully stamped the notes contained in the ID Table.

ERR_DIRECTORY - This function is inappropriate for directories.

ERR_NO_STAMPED_NOTES - No documents were categorized(stamped).  

ERR_NOACCESS - You are not authorized to modify one or more of the documents specified.  Only those documents you are authorized to modify have been stamped.

ERR_xxx - Errors returned by lower level Notes functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


**Sample Usage :**
```


   /* Please note that the first WORD of text_item_value was already */
   /* set to TYPE_TEXT and text_item_size was adjusted accordingly.  */

       case STAMP_NOTES:
            printf(" will be Stamped\n");
            if (!(dataset_state & HAVE_CATEGORY))
            {
                printf("You must supply a category for action: -C\n");
                goto Exit;
            }
            if ( error_status = NSFDbStampNotes(db_handle_src,
                                 idtable_handle, CATEGORIES_ITEM_NAME,
                                 strlen(CATEGORIES_ITEM_NAME),
                                 text_item_value,
                                 text_item_size))
                goto Exit;
            break;

```
**See Also :**
[NSFDbGetModifiedNoteTable](D:/md_files/NSFDbGetModifiedNoteTable.md)
[NIFOpenCollection](D:/md_files/NIFOpenCollection.md)
---
