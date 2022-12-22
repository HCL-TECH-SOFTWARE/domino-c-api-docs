




<!--
 /\* Font Definitions \*/
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




**Initial Release 6**



**Function : Item (Field)**



**NSFItemInfoPrev** **- Get
information about the previous item in a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemInfoPrev(**  

      NOTEHANDLE  note\_handle,  

      BLOCKID  CurrItem,  

      const char far \*item\_name,  

      WORD  name\_len,  

      BLOCKID far \*item\_blockid\_ptr,  

      WORD far \*value\_type\_ptr,  

      BLOCKID far \*value\_blockid\_ptr,  

      DWORD far \*value\_len\_ptr**);**



**Description :**



This
function looks for the previous item (field) in a note.  The function returns a
variety of information -- enabling you to access each item's contents.  

  

The BLOCKID values obtained using this function refer to memory within a note. 
This memory is managed by Domino and Notes, and should not be freed by the
application.  

  

Note: The items in a note are maintained in the order that they were added to
the note. You cannot depend on this function to obtain items in the same order
in which they appear in any form.   

  

Note: To find all the items in a note, use NSFItemScan.


 


**Parameters :**



Input :  

note\_handle  -  A handle to the open note you want to look in.  

  

CurrItem  -  The BLOCKID of the item that occurs after the one you are
interested in.  

  

item\_name  -  The name of the item you want to retrieve. If you specify this
argument, the function will not find any items except ones with this name. If
you set this argument to NULL, the function will retrieve the next item
regardless of its name.  

  

name\_len  -  The length of item\_name.  If the previous argument is NULL, then
this value must be set to zero (0).  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Item info successfully obtained.  

  

ERR\_ITEM\_NOT\_FOUND - If the item\_name argument is NULL, then there are no more
items stored in the note.  If the item\_name argument is not NULL, then there
are no more items with this name.  

  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  

item\_blockid\_ptr  -  The address of a BLOCKID in which the pool and block of
the next item is returned.  This BLOCKID can be used to get more information
(such as the item's name) about the item via NSFItemQuery.  Set this argument
to NULL if you don't want this information.   

  

value\_type\_ptr  -  The address of a WORD in which the data type of the item's
value is returned. The data types are defined in TYPE\_xxx.   In the case where
ERR\_ITEM\_NOT\_FOUND is returned by NSFItemInfoNext(), this argument is always
set to TYPE\_INVALID\_OR\_UNKNOWN.    

  

value\_blockid\_ptr  -  The address of a BLOCKID in which the BLOCKID associated
with the item's value is returned.  Call OSLockBlock to lock the BLOCKID and
obtain an actual address.  The first 2 bytes pointed to are the item's datatype
WORD, followed by the item's actual value. The data type word is always in host
(machine-specific) format.  The remainder of the data is also in host format,
unless the data type is one of:  TYPE\_COMPOSITE, TYPE\_COLLATION, TYPE\_OBJECT,
TYPE\_VIEW\_FORMAT, TYPE\_ICON, TYPE\_SIGNATURE, TYPE\_SEAL, TYPE\_SEALDATA,
TYPE\_SEAL\_LIST, TYPE\_WORKSHEET\_DATA, or TYPE\_USERDATA. If the item is one of
these data types, you must convert the data structures in the item's value from
Domino canonical format to host format before accessing the members of those
structures.  

  

value\_len\_ptr  -  The address of a DWORD in which the length of the item's
value (including the WORD of data type) is returned.  

  




 **See Also :**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFItemInfoNext](NSFItemInfoNext.md)**


**[NSFItemQuery](NSFItemQuery.md)**


**[NSFItemScan](NSFItemScan.md)**


**[ODSReadMemory](ODSReadMemory.md)**


**[OSLockBlock](OSLockBlock.md)**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





