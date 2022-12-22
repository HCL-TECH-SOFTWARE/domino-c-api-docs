




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




 


**Function : Item (Field)**



**NSFItemAppendByBLOCKID** **- Adds an
item value to a note by BLOCKID.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemAppendByBLOCKID(**  

      NOTEHANDLE  note\_handle,  

      WORD  item\_flags,  

      const char far \*item\_name,  

      WORD  name\_len,  

      BLOCKID  value\_bid,  

      DWORD  value\_len,  

      BLOCKID far \*item\_bid\_ptr**);**



**Description :**



This
function adds an item (field) to the in-memory copy of a note using the BLOCKID
of the item value. Call NSFNoteUpdate to write the modified note to disk.  

  

Unlike NSFItemAppend, NSFItemAppendByBLOCKID does not copy the memory
associated with the value BLOCKID. Instead, it transfers ownership of memory to
the note. Unlock the memory associated with the BLOCKID but do not free it.
NSFNoteClose will free the memory. Warning: to avoid associating the same
memory with more than one note, do not use a BLOCKID obtained by calling
NSFItemInfo with the handle to a different note.  

  

Use this function to append an item to a note if you happen to have the item
data in a Domino memory block. Otherwise, it is generally more convenient to
use NSFItemAppend.  

  

API programs on a non-Intel architecure machines must convert the item value to
Domino Canonical Format before calling NSFItemAppend if value\_bid is one of the
following:   

  

    TYPE\_COMPOSITE  

    TYPE\_COLLATION  

    TYPE\_OBJECT  

    TYPE\_VIEW\_FORMAT  

    TYPE\_ICON  

    TYPE\_SIGNATURE  

    TYPE\_SEAL  

    TYPE\_SEALDATA  

    TYPE\_SEAL\_LIST  

    TYPE\_WORKSHEET\_DATA  

    TYPE\_USERDATA  

  

Use ODSWriteMemory() to convert item data from host specific format to Domino
canonical format before calling NSFItemAppendByBLOCKID.  

  

Note that the data type word - - the first word in the memory object specified
by value\_bid - - is in Host specific format, not Domino Canonical Format.


 


**Parameters :**



Input :  

note\_handle  -  The handle to the note that will receive this item.  

  

item\_flags  -   The flags that define the characteristics of this item. These
flags are defined in ITEM\_xxx and may be bitwise or'ed together for combined
functionality.  

  

item\_name  -  Text buffer containing the name of the item as it will appear in
the note. This name is equivalent to the field name when you design a form
using the screen interface.  

  

name\_len  -  The length of item\_name.  

  

value\_bid  -  The BLOCKID of a Domino memory block that contains the item's
datatype word followed by the item value.  The data type word is always in host
format. The item value data following the data type word must be in Domino
canonical format only if the data type is one of  TYPE\_COMPOSITE, TYPE\_COLLATION,
TYPE\_OBJECT, TYPE\_VIEW\_FORMAT, TYPE\_ICON, TYPE\_SIGNATURE, TYPE\_SEAL,
TYPE\_SEALDATA, TYPE\_SEAL\_LIST, TYPE\_WORKSHEET\_DATA, or TYPE\_USERDATA.  

  

value\_len  -  Length of the memory object in BYTES, including the Domino data
type WORD.  

  




Output :  

(routine)  -  Return status from this call.    

  

NOERROR - Successfully appended Item to the note.  

  

ERR\_xxx - Errors returned by lower level functions. Use OSLoadString to convert
the status to a message string and display the string to the user.  

  

  

item\_bid\_ptr  -  The specified location gets the item BLOCKID of the newly
appended item (field).  You may need the item BLOCKID in API routines such as
NSFItemInfoNext and NSFItemDeleteByBLOCKID. Specify NULL if you do not wish
this value to be returned.  This block is part of the memory allocated for the
note, and is managed by Domino and Notes;  the application should not free this
block.  

  




 **Sample Usage :**


  

   /\* Fabricate an Item and append it to Note2 by BLOCKID  \*/  

  

   if (error\_status = OSMemAlloc(0, LINEOTEXT, &fab\_value\_bid.pool))  

       goto Exit;  

   else  

       cleanup\_state += FREE\_BIDMEM;  

  

   fab\_value\_bid.block = NULLBLOCK;  

   value\_ptr = OSLockBlock(char, fab\_value\_bid);  

   cleanup\_state += UNLOCK\_BIDMEM;  

  

   \*(WORD \*) value\_ptr = TYPE\_TEXT;  

   value\_ptr += sizeof(WORD);  

   strcpy(value\_ptr, "What a Country!");  

  

   value\_len = strlen(value\_ptr) + sizeof(WORD);  

   item\_flags = ITEM\_SUMMARY;  

  

   OSUnlockBlock(fab\_value\_bid);  

   cleanup\_state -= UNLOCK\_BIDMEM;  

  

   if (error\_status=NSFItemAppendByBLOCKID(note2\_handle, item\_flags,  

                               TEXT\_ITEM, strlen(TEXT\_ITEM),  

                               fab\_value\_bid, value\_len, NULL))  

       goto Exit;  

  




 **See Also :**


**[ITEM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00F200B70087008C85255E2D007931E6)**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFItemQuery](NSFItemQuery.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[NSFNoteUpdate](NSFNoteUpdate.md)**


**[OSLockBlock](OSLockBlock.md)**


**[OSMemAlloc](OSMemAlloc.md)**


**[OSUnlockBlock](OSUnlockBlock.md)**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





