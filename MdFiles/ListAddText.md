




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



**ListAddText** **- Add a
string to a empty text list entry.**


**----------------------------------------------------------------------------------------------------------**



**#include <textlist.h>**



STATUS
LNPUBLIC **ListAddText(**  

      void far \*pList,  

      BOOL  fPrefixDataType,  

      WORD  EntryNumber,  

      const char far \*Text,  

      WORD  TextSize**);**



**Description :**



This
function adds a string to an entry in a text list that does not currently have
a string associated with it.  The list must be of sufficient size, so that the
unused portion can accommodate the new text string.  Use ListAddEntry if there
is not already pre-allocated space for the new text string to be added to an
existing entry.  

  

This function may be used to add text to an existing text list item.  First use
OSLockBlock on the value\_blockid returned by NSFItemInfo for the text list
item.  The pointer returned by OSLockBlock contains the address of the text
list within the note.  ListAddText can then be used to add the new text string
to the text list item.  

  

This function can be used to substitute text for a list entry if the old and
new text strings are the same length.


 


**Parameters :**



Input :  

pList  -  Pointer to memory containing the original text list.  

  

fPrefixDataType  -  BOOL indicating whether or not the list is prefixed with a
WORD containing the Domino data type.  TRUE when using a pointer value derived
from a BLOCKID obtained from NSFItemInfo or FALSE if using a pointer value to a
newly created list, that will later be added to a note using NSFItemAppend.  

  

EntryNumber  -  WORD containing the entry number (0-based) to be used.  The
value must fall between 0 and (ListGetNumEntries - 1).  

  

Text  -  Pointer to memory containing LMBCS characters.  The string does not
have to be null-terminated.  

  

TextSize  -  WORD containing the length of the string.  Strings added to the
list may be of varying length, but in no case should the length of the new
string exceed the amount of available storage in the list.  This amount can be
determined using the following algorithm:  ListGetSize - sizeof(LIST) -
(sizeof(WORD) \* ListGetNumEntries).  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:  

  

NOERROR - string successfully added to text list.  

ERR\_MARKERS\_FOLLOW - string was too large, overwrote non-list memory.  

  

  

pList  -  Pointer to memory containing the updated text list.  

  




 **Sample Usage :**


  

   if (error\_status = ListAddText(old\_list\_ptr, old\_prefix\_flag,  

                                  FIRST\_ENTRY,  

                                  STRINGX, strlen(STRINGX)))  

       goto Exit;  

  




 **See Also :**


**[ListAllocate](ListAllocate.md)**


**[ListGetText](ListGetText.md)**


**[ListRemoveEntry](ListRemoveEntry.md)**


**[ListAddEntry](ListAddEntry.md)**


**[ListGetSize](ListGetSize.md)**


**[ListGetNumEntries](ListGetNumEntries.md)**



----------------------------------------------------------------------------------------------------------


 





