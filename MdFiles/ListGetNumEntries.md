




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



**ListGetNumEntries** **- Returns
the number of entries in a text list.**


**----------------------------------------------------------------------------------------------------------**



**#include <textlist.h>**



WORD
LNPUBLIC **ListGetNumEntries(**  

      void far \*vList,  

      BOOL  NoteItem**);**



**Description :**



This
function takes the list pointer and a data type prefix flag.  It returns the
number of entries in the text list.  The number returned can be used as the
entry number argument to the ListAddEntry function to insure the appropriate
entry number is provided to that function call.


 


**Parameters :**



Input :  

vList  -  A pointer to an existing text list.  

  

NoteItem  -  BOOL indicating presence of a Domino data type prefix.   Use FALSE
if the first argument is a list that is later going to used in conjunction with
NSFItemAppend. Use TRUE if you obtained the list's item and value BLOCKIDs with
NSFItemInfo and wish to find out how many entries there are in the list.  

  




Output :  

(routine)  -  Returns number of entries in the text list.  

  

  




 **Sample Usage :**


  

   if(error\_status = ListAddEntry(list\_handle, prefix\_flag,&list\_size,  

                               ListGetNumEntries(list\_ptr,prefix\_flag),  

                               STRING2, strlen(STRING2)))  

        goto Exit;  

  




 **See Also :**


**[ListAddEntry](ListAddEntry.md)**


**[ListAddText](ListAddText.md)**


**[ListAllocate](ListAllocate.md)**


**[ListGetSize](ListGetSize.md)**


**[ListGetText](ListGetText.md)**


**[ListRemoveEntry](ListRemoveEntry.md)**



----------------------------------------------------------------------------------------------------------


 





