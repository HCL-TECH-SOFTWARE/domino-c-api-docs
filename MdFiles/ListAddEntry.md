




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



**ListAddEntry** **- Add a
string to a text list.**


**----------------------------------------------------------------------------------------------------------**



**#include <textlist.h>**



STATUS
LNPUBLIC **ListAddEntry(**  

      DHANDLE  hList,  

      BOOL  fPrefixDataType,  

      WORD far \*pListSize,  

      WORD  EntryNumber,  

      const char far \*Text,  

      WORD  TextSize**);**



**Description :**



This
function adds a string to a text list in memory, increasing number of entries
in the list if necessary. This re-allocates the storage associated with the the
text list to the original size plus the specified text size plus one more word
for the entry length.   

  




The hlist
does not have to be unlocked before this call.  However, this function may move
the memory object to increase the size of the list.  Therefore, after returning
from this function and before referencing any pointers to the text list, the
caller MUST refresh all pointers to the text list by unlocking the list handle
(OSUnlockObject)and then relocking the list handle (OSLockObject).  It is
recommended that you unlock the list handle after the call to ListAllocate and
relock the list handle before subsequent references to the text list pointer.  

  

This function can not be used to increase the size of a text list item that is
already part of a note, as the value.blockid.pool member is not the equivalent
of an hList.


 


**Parameters :**



Input :  

hList  -  HANDLE to a Domino memory object containing text list.  This handle
must have been created with ListAllocate.  ListAddEntry does not require that
the list be unlocked at the time of the call.  

  

fPrefixDataType  -  BOOL indicating whether or not the list is prefixed with a
WORD containing the Domino data type.  The value should be FALSE when used in
association with a HANDLE to a newly created list, that will later be added to
a note using NSFItemAppend.  

  

pListSize  -  Address of the WORD variable containing the current list size.  

  

EntryNumber  -  WORD containing the value returned by a call to
ListGetNumEntries.  Since the entry number is 0-based, the value will always be
equal to the next available EntryNumber.  

  

Text  -  Address of the string to be added to the text list.  This string does
not have to be null-terminated.  

  

TextSize  -  WORD containing the number of bytes in the string.  

  




Output :  

(routine)  -  Return indicates either sucess or what the error is. The return
codes include:  

  

NOERROR - list entry was successfully added.  

ERR\_MEMORY - Not enough global memory available for allocation.  

ERR\_SEGMENT\_TOO\_BIG - Requested size is greater than the maximum supported
(60K).  

  

  

pListSize  -  Address of the WORD variable containing the new list size.  

  




 **Sample Usage :**


ListAllocate(0, 0,
FALSE, &hList, &pList, &wListSize);


NumEntries
= ListGetNumEntries(pList, FALSE)


OSUnlockObject(hList);



 


ListAddEntry(hList,
FALSE, &wListSize,


            
NumEntries,  


            
"NewTextListEntry",


             
strlen("NewTextListEntry"));


pList =
OSLockObject (hList);


 


NSFItemAppend(hNote,
ITEM\_SUMMARY, FieldName,


             
FieldNameLen, TYPE\_TEXT\_LIST,


             
pList, wListSize);


OSUnlockObject(hList);


OSMemFree
(hList);


 **See Also :**


**[ListAddText](ListAddText.md)**


**[ListAllocate](ListAllocate.md)**


**[ListGetNumEntries](ListGetNumEntries.md)**


**[ListGetSize](ListGetSize.md)**


**[ListRemoveAllEntries](ListRemoveAllEntries.md)**


**[ListRemoveEntry](ListRemoveEntry.md)**



----------------------------------------------------------------------------------------------------------


 





