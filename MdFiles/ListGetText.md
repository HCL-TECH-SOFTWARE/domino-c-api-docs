




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




 


**Function : Text List Manipulation**



**ListGetText** **- Obtain a
string from a text list.**


**----------------------------------------------------------------------------------------------------------**



**#include <textlist.h>**



STATUS
LNPUBLIC **ListGetText(**  

      void far \*pList,  

      BOOL  fPrefixDataType,  

      WORD  EntryNumber,  

      char far \* far \*retTextPointer,  

      WORD far \*retTextLength**);**



**Description :**



This
function obtains a specific entry from an existing text list, then returns that
text entry and its length.  If OSLockBlock is used with a value\_blockid
returned by NSFItemInfo, the pointer returned by OSLockBlock contains the
address of the text list within the text list item of the existing note.  This
function can then be used to obtain any string already in the text list item. 


 


**Parameters :**



Input :  

pList  -  Pointer to memory containing the text list.  

  

fPrefixDataType  -  BOOL indicating whether or not the list is prefixed with a
WORD containing the Domino data type.  TRUE when using a pointer value derived
from a BLOCKID obtained from NSFItemInfo or FALSE if using a pointer value to a
newly created list, that will later be added to a note using NSFItemAppend.  

  

EntryNumber  -  WORD containing the index (0-based) of the entry to
retrieved.   The value should always be in a range between 0 and the value
returned by (ListGetNumEntries - 1).  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:  

  

NOERROR - list entry was successfully located.  

ERR\_ODS\_NO\_SUCH\_ENTRY -  no such entry in the text list.  

  

  

retTextPointer  -  The address of a pointer in which a pointer to the requested
text list entry is returned.  The text must then be copied/moved to
pre-allocated storage.  The NULL terminator is not provided by the function.  

  

retTextLength  -  The address of a WORD in which the size of the text list
entry is returned.  This can be used to place a NULL terminator if you intend
to create a null-terminated string using the text list entry.  

  




 **Sample Usage :**


  

   for (curr\_entry\_num = FIRST\_ENTRY; curr\_entry\_num < last\_entry\_num;  

        curr\_entry\_num++)  

   {  

       if (error\_status = ListGetText(old\_list\_ptr, old\_prefix\_flag,  

                                      curr\_entry\_num,  

                                      &string\_ptr, &string\_length))  

           break;  

       if (error\_status = ListAddEntry (list\_handle, prefix\_flag,  

                                        &list\_size, curr\_entry\_num,  

                                        string\_ptr, string\_length))  

           break;  

   }  

  




 **See Also :**


**[ListAllocate](ListAllocate.md)**


**[ListAddEntry](ListAddEntry.md)**


**[ListAddText](ListAddText.md)**


**[ListRemoveEntry](ListRemoveEntry.md)**


**[ListGetSize](ListGetSize.md)**


**[ListGetNumEntries](ListGetNumEntries.md)**



----------------------------------------------------------------------------------------------------------


 





