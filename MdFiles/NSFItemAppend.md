




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



**NSFItemAppend** **- Adds an
item (field) to an open note using the item name.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemAppend(**  

      NOTEHANDLE  note\_handle,  

      WORD  item\_flags,  

      const char far \*item\_name,  

      WORD  name\_len,  

      WORD  item\_type,  

      const void far \*item\_value,  

      DWORD  value\_len**);**



**Description :**



This
function adds an item (field) to an open note. It does not update the Domino
database file on disk. To write the modified note to the database file on disk,
you must call NSFNoteUpdate after appending all items to the note.  

  

NSFItemAppend is a flexible, low-level way to add an item to a note. You must
specify, as input, the item name, the data, the data type, and the data
length.  The API also provides less flexible, higher-level functions such as
NSFItemSetText for appending items of specific data types.  

  

NSFItemAppend creates an item header and adds this item header to a queue
associated with the open note. You may append any number of items to a note
through repeated calls to NSFItemAppend. NSFItemAppend also allocates a block
of memory to store the item value. It copies the number of bytes specified by
value\_len from the buffer specified by item\_value into this memory block. This
means that after NSFItemAppend has returned, your program may free the memory
specified by item\_value.  

  

The data pointed to by item\_value does not begin with the data type word.  The
format of the data pointed to by item\_value depends on the data type. The
reference manual entry for each data type specifies the format of the item
value.  

  

For each of the following data types, the data pointed to by item\_value must be
in Domino canonical format.  Your program must convert the item value to Domino
canonical Format before calling NSFItemAppend if (1) your program runs on a
non-Intel architecture machine, and (2) item\_type is one of the following data
types:   

  

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

  

Use ODSWriteMemory() to convert item data from machine-specific (host) format
to Domino canonical format before calling NSFItemAppend.


 


**Parameters :**



Input :  

note\_handle  -  The handle to the note that will receive this item.  

  

item\_flags  -  The flags that define the characteristics of this item. These
flags are defined in ITEM\_xxx and may be bitwise or'ed together for combined
functionality.  

  

item\_name  -  The name of the item in the note. This name is equivalent to the
field name when you design a form using the screen interface.   

  

name\_len  -  The length of item\_name.  

  

item\_type  -  The type of data in this item. Item types are defined in
TYPE\_xxx.  

  

item\_value  -  A pointer to the value (excluding the data type word).  If the
API program is running on a non-Intel architecture system and item\_type is one
of the data types listed above, then the data pointed to by item\_value must be
in Domino canonical format.  

  

value\_len  -  The length of the item's value (excluding the data type word).
The length must not exceed 64K bytes. If the ITEM\_SUMMARY flag is set in
item\_flags, then value\_len must not exceed 32K.  

  




Output :  

(routine)  -  cReturn status from this call:   

  

NOERROR - Successfully appended Item to the note.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error status as a string that you may display/log for the user.  

  

  




 **Sample Usage :**


  

  

   /\* Prepare to and then append the text list \*/  

  

   list\_size    = ListGetSize (list\_ptr, prefix\_flag);  

   if (error\_status = NSFItemAppend(note\_handle,0,  

                               "Form", strlen("Form"),  

                               TYPE\_TEXT, argv[2],  

                               (DWORD) strlen(argv[2])))  

       goto Exit;  

   if (error\_status = NSFItemAppend(note\_handle,ITEM\_SUMMARY,  

                               ITEM\_NAME, strlen(ITEM\_NAME),  

                               TYPE\_TEXT\_LIST, list\_ptr,  

                               (DWORD) list\_size))  

       goto Exit;  

  




 **See Also :**


**[ITEM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00F200B70087008C85255E2D007931E6)**


**[NSFItemAppendByBLOCKID](NSFItemAppendByBLOCKID.md)**


**[NSFItemDelete](NSFItemDelete.md)**


**[NSFItemDeleteByBLOCKID](NSFItemDeleteByBLOCKID.md)**


**[NSFItemSetNumber](NSFItemSetNumber.md)**


**[NSFItemSetText](NSFItemSetText.md)**


**[NSFItemSetTime](NSFItemSetTime.md)**


**[ODSLength](ODSLength.md)**


**[ODSWriteMemory](ODSWriteMemory.md)**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





