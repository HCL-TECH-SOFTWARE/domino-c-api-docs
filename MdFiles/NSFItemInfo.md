




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



**NSFItemInfo** **- Get
information about an item (field) in a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemInfo(**  

      NOTEHANDLE  note\_handle,  

      const char far \*item\_name,  

      WORD  name\_len,  

      BLOCKID far \*item\_blockid,  

      WORD far \*value\_datatype,  

      BLOCKID far \*value\_blockid,  

      DWORD far \*value\_len**);**



**Description :**



This
function gets information about a particular item (field) in a note. The
function's inputs are a handle to an open note and the name of the field you are
looking for. It yields the item header, the data type, the item's value, and
the length of the item's value.  

  

Items in a note are ordered. You can get information about the first item in
the note, regardless of its name, by specifying NULL for the field name.  

  

The BLOCKID values obtained using this function refer to memory within a note. 
This memory is managed by Domino and Notes, and should not be freed by the
application.


 


**Parameters :**



Input :  

note\_handle  -  A handle to the open note you want to look in.  

  

item\_name  -  The name of the item (field) you want information about. To get
information about the first field in the note, regardless of its name, set this
argument to NULL.  

  

name\_len  -  The length of item\_name. If the item\_name is NULL, set this argument
to zero.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_ITEM\_NOT\_FOUND  

  

  

item\_blockid  -  The address of a BLOCKID in which the pool and block of an
item's header is returned. Set this argument to NULL if you don't want this
information. You need the BLOCKID of the item's header to pass as input
arguments to API functions such as NSFItemInfoNext, NSFItemQuery, NSFItemCopy,
and NSFItemDeleteByBLOCKID.  

  

value\_datatype  -  The address of a WORD in which the data type of the item's
value is returned. The data types are defined in TYPE\_xxx.  In the case where
ERR\_ITEM\_NOT\_FOUND is returned by NSFItemInfo(), this argument is always set to
TYPE\_INVALID\_OR\_UNKNOWN.    

  

value\_blockid  -  The address of a BLOCKID in which the pool and block of the
item's value (the actual contents of the field) is returned. You must call
OSLockBlock to translate the BLOCKID into an actual address.  The first 2 bytes
pointed to are the item's datatype WORD, followed by the item's actual value.
The data type word is always in host (machine-specific) format.  The remainder
of the data is also in host format, unless the data type is one of: 
TYPE\_COMPOSITE, TYPE\_COLLATION, TYPE\_OBJECT, TYPE\_VIEW\_FORMAT, TYPE\_ICON, TYPE\_SIGNATURE,
TYPE\_SEAL, TYPE\_SEALDATA, TYPE\_SEAL\_LIST, TYPE\_WORKSHEET\_DATA, or
TYPE\_USERDATA. If the item is one of these data types, you must convert the
data structures in the item's value from Domino canonical format to host format
before accessing the members of those structures.  

  

value\_len  -  The address of a DWORD in which the length of the item's value is
returned.  The length of the datatype WORD that precedes the value is always
included in the length that is returned.  

  




 **Sample Usage :**


   /\* Obtain the old
list \*/  

  

   if (error\_status = NSFItemInfo(note\_handle, ITEM\_NAME,  

                                  strlen(ITEM\_NAME), &item\_bid,  

                                  &value\_datatype, &value\_bid,  

                                  &value\_size))  

       goto Exit;  

  

   old\_list\_ptr = OSLockBlock(char, value\_bid);  

  

   if (old\_list\_ptr != NULL)  

       cleanup\_state += UNLOCK\_VALUEBID;  

  

  /\* Step over the data type word to point to the actual data \*/  

   old\_list\_ptr += sizeof(WORD);  

  




 **See Also :**


**[NSFItemInfoNext](NSFItemInfoNext.md)**


**[NSFItemScan](NSFItemScan.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[ODSReadMemory](ODSReadMemory.md)**


**[ODSWriteMemory](ODSWriteMemory.md)**


**[OSLockBlock](OSLockBlock.md)**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





