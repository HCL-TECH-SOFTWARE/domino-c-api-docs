




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




**Initial Release 4.0**



**Function : Text List Manipulation**



**ListRemoveAllEntries** **- Remove
all entries from a text list.**


**----------------------------------------------------------------------------------------------------------**



**#include <textlist.h>**



STATUS
LNPUBLIC **ListRemoveAllEntries(**  

      DHANDLE  hList,  

      BOOL  fPrefixDataType,  

      WORD far \*pListSize**);**



**Description :**



Remove all
the entries from the text list.  During the removal process, the Domino memory
object containing the list is re-allocated and the size will be reduced to the
minimum size for a text list.  If you had previously locked the list handle to
obtain a pointer to the text list, be aware that this pointer may no longer
valid after calling ListRemoveAllEntries().   You must unlock the list handle
and then re-lock the list handle after the call to ListRemoveAllEntries(), if
you need to reference the pointer to the text list.


 


**Parameters :**



Input :  

hList  -  HANDLE to a Domino memory object containing text list.  This handle
must have been created with ListAllocate.  ListAddEntry does not require that
the list be unlocked at the time of the call.  

  

fPrefixDataType  -  BOOL indicating whether or not the list is prefixed with a
WORD containing the Domino data type.  

  

pListSize  -  Address of the WORD variable containing the current list size.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

pListSize  -  Address of the WORD variable containing the new list size.  

  




 **See Also :**


**[ListAddEntry](ListAddEntry.md)**


**[ListAddText](ListAddText.md)**


**[ListAllocate](ListAllocate.md)**


**[ListGetNumEntries](ListGetNumEntries.md)**


**[ListGetSize](ListGetSize.md)**


**[ListRemoveEntry](ListRemoveEntry.md)**



----------------------------------------------------------------------------------------------------------


 





