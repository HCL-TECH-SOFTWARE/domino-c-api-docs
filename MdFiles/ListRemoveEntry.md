




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



**ListRemoveEntry** **- Remove an
entry from a text list.**


**----------------------------------------------------------------------------------------------------------**



**#include <textlist.h>**



STATUS
LNPUBLIC **ListRemoveEntry(**  

      DHANDLE  hList,  

      BOOL  fPrefixDataType,  

      WORD far \*pListSize,  

      WORD  EntryNumber**);**



**Description :**



This
function removes the requested entry from a text list created by ListAllocate. 
During the removal process, the Domino memory object containing the list is
re-allocated and reduced in size by an amount corresponding the length of the
text entry and its related header overhead.  If you had previously locked the
list handle to obtain a pointer to the text list, be aware that this pointer
may no longer valid after calling ListRemoveEntry().   You must unlock the list
handle and then re-lock the list handle after the call to ListRemoveEntry(), if
you need to reference the pointer to the text list.


 


This
function can not be used to decrease the size of a text list item that is
already part of a note, as the value\_blockid.pool member is not the equivalent
of an hList.


 


**Parameters :**



Input :  

hList  -  HANDLE to memory object containing text list.  This handle must have
been returned by ListAllocate.  

  

fPrefixDataType  -  BOOL indicating whether or not the list is prefixed with a
WORD containing the Domino data type.  Should be FALSE when using a HANDLE to a
newly created list that will later be added to a note using NSFItemAppend.  

  

pListSize  -  Address of the WORD variable containing the current size of the
text list.  

  

EntryNumber  -  WORD containing index (0-based) of entry to be removed.  Should
be in the range of 0 through (ListGetNumEntries - 1).  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:  

  

NOERROR - list entry was successfully removed.  

ERR\_ODS\_NO\_SUCH\_ENTRY -  no such entry in the text list.  

  

  

pListSize  -  Address of the WORD in which the new size of the text list,
including  related overhead is returned  

  




 **Sample Usage :**


  

   if (error\_status = ListRemoveEntry (list\_handle, prefix\_flag,  

                                    &list\_size, SECOND\_ENTRY))  

       goto Exit;  

  




 **See Also :**


**[ListAllocate](ListAllocate.md)**


**[ListAddEntry](ListAddEntry.md)**


**[ListAddText](ListAddText.md)**


**[ListGetSize](ListGetSize.md)**


**[ListGetNumEntries](ListGetNumEntries.md)**



----------------------------------------------------------------------------------------------------------


 





