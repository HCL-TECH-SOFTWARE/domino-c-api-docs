##### Function : Item (Field)
##### NSFItemInfoNext - Get information about the next item in a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFItemInfoNext(

	NOTEHANDLE  note_handle,
	BLOCKID  NextItem,
	const char far *item_name,
	WORD  name_len,
	BLOCKID far *item_blockid_ptr,
	WORD far *value_type_ptr,
	BLOCKID far *value_blockid_ptr,
	DWORD far *value_len_ptr);
```
**Description :**

This function looks for the next item (field) in a note. The function is used 
primarily to find all the items in a note that have the same name. The function 
returns a variety of information -- enabling you to access each item's contents.

The BLOCKID values obtained using this function refer to memory within a note.  
This memory is managed by Domino and Notes, and should not be freed by the 
application.

Note: The items in a note are maintained in the order that they were added to 
the note. You cannot depend on this function to obtain items in the same order 
in which they appear in any form. 

Note: To find all the items in a note, use NSFItemScan.

**Parameters :**
Input :
note_handle  -  A handle to the open note you want to look in.

NextItem  -  The BLOCKID of the item that occurs before the one you are interested in.

item_name  -  The name of the item you want to retrieve. If you specify this argument, the function will not find any items except ones with this name. If you set this argument to NULL, the function will retrieve the next item regardless of its name.

name_len  -  The length of item_name.  If the previous argument is NULL, then this value must be set to zero (0).

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Item info successfully obtained.

ERR_ITEM_NOT_FOUND - If the item_name argument is NULL, then there are no more items stored in the note.  If the item_name argument is not NULL, then there are no more items with this name.

ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


item_blockid_ptr  -  The address of a BLOCKID in which the pool and block of the next item is returned.  This BLOCKID can be used to get more information (such as the item's name) about the item via NSFItemQuery.  Set this argument to NULL if you don't want this information. 

value_type_ptr  -  The address of a WORD in which the data type of the item's value is returned. The data types are defined in TYPE_xxx.   In the case where ERR_ITEM_NOT_FOUND is returned by NSFItemInfoNext(), this argument is always set to TYPE_INVALID_OR_UNKNOWN.  

value_blockid_ptr  -  The address of a BLOCKID in which the BLOCKID associated with the item's value is returned.  Call OSLockBlock to lock the BLOCKID and obtain an actual address.  The first 2 bytes pointed to are the item's datatype WORD, followed by the item's actual value. The data type word is always in host (machine-specific) format.  The remainder of the data is also in host format, unless the data type is one of:  TYPE_COMPOSITE, TYPE_COLLATION, TYPE_OBJECT, TYPE_VIEW_FORMAT, TYPE_ICON, TYPE_SIGNATURE, TYPE_SEAL, TYPE_SEALDATA, TYPE_SEAL_LIST, TYPE_WORKSHEET_DATA, or TYPE_USERDATA. If the item is one of these data types, you must convert the data structures in the item's value from Domino canonical format to host format before accessing the members of those structures.

value_len_ptr  -  The address of a DWORD in which the length of the item's value (including the WORD of data type) is returned.


**Sample Usage :**
```
/* This code fragment illustrates how to obtain access to a 
    number of items in a note which have the same item name. 
*/

   num_fields = 0;     /* initialize counter for number of fields
                          found */

   /* get information about a field called RICH_TEXT */

   error = NSFItemInfo(note_handle, 
                       "RICH_TEXT", 
                       strlen("RICH_TEXT"), 
                       &item_blockid,
                       &value_datatype, NULL, NULL);

   if (error)
   {
      printf ("Error:  unable to get info about item 'RICH_TEXT'\n");
      NSFNoteClose (note_handle);
      NSFDbClose(db_handle);
      return (ERR(error));
   }

   printf("Field 'RICH_TEXT' was found.  Type = %s.\n",
           interpret_datatype(value_datatype));
   num_fields++;

   /* get information about additional fields with the 
      same name, RICH_TEXT */

   while (TRUE)
   {
      prev_item_blockid = item_blockid; 

      error = NSFItemInfoNext(note_handle, 
                              prev_item_blockid, 
                              "RICH_TEXT",  /* name of item we want
                                               next; obtain items in
                                               in order in note */
                              strlen("RICH_TEXT"),  /* name length */
                              &item_blockid,
                              &value_datatype,
                              &value_blockid,
                              &value_len);

      if (ERR(error) == ERR_ITEM_NOT_FOUND)
      {
          /* NSFItemInfoNext returned ERR_ITEM_NOT_FOUND. */
          printf ("No more items found in note.\n");
          break;
      }
      else if (error)
      {
          printf
           ("Error: unable to get info about next item in note.\n");
          break;
      }

      /* get name of field */

      NSFItemQuery(note_handle, 
                   item_blockid,  /* block ID of item to get name of */
                   item_name,      /* name of item returned here */
                   LINEOTEXT,
                   &item_name_len, /* length of name returned here */
                   &item_flags,    /* item flags returned here */
                   &value_datatype,
                   &value_blockid,
                   &value_len);

      /* print name and type of field */

      item_name[item_name_len] = '\0';

      printf ("Field '%s' was found.  Type = %s.\n", item_name, 
                          interpret_datatype(value_datatype));
      num_fields++;

  }   /* end of while loop */


  printf("%d fields found.\n", num_fields);

```
**See Also :**
[NSFItemInfo](/domino-c-api-docs/reference/Func/NSFItemInfo)
[NSFItemInfoPrev](/domino-c-api-docs/reference/Func/NSFItemInfoPrev)
[NSFItemQuery](/domino-c-api-docs/reference/Func/NSFItemQuery)
[NSFItemScan](/domino-c-api-docs/reference/Func/NSFItemScan)
[ODSReadMemory](/domino-c-api-docs/reference/Func/ODSReadMemory)
[OSLockBlock](/domino-c-api-docs/reference/Func/OSLockBlock)
[TYPE_xxx](/domino-c-api-docs/reference/Symb/TYPE_xxx)
---
