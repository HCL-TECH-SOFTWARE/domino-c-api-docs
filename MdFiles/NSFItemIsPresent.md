




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



**NSFItemIsPresent** **- Return
TRUE if an Item is present in a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



BOOL **NSFItemIsPresent(**  

      NOTEHANDLE  note\_handle,  

      char far \*item\_name,  

      WORD  item\_name\_length**);**



**Description :**



This function
takes a handle to an open note and the name for the Item whose presence you
wish to confirm, and the length of that name.  If the Item is present it
returns TRUE.


 


**Parameters :**



Input :  

note\_handle  -  A handle to an open note in memory.  

  

item\_name  -  A pointer to an Item name string.  

  

item\_name\_length  -  The length of the item\_name string.  

  




Output :  

(routine)  -  TRUE - If named Item is present in the open note.  FALSE - If
named item is NOT present in the open note.  

  

  




 **Sample Usage :**


  

  /\* Print ULONG ITEM \*/  

   

  if (NSFItemIsPresent(note1\_handle,ULONG\_ITEM, strlen(ULONG\_ITEM)))  

       printf("%s: %lu\n", ULONG\_ITEM,  

              (NSFItemGetLong(note1\_handle, ULONG\_ITEM, 0L)));  

  

  




 **See Also :**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFItemInfoNext](NSFItemInfoNext.md)**


**[NSFItemQuery](NSFItemQuery.md)**


**[NSFItemScan](NSFItemScan.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**



----------------------------------------------------------------------------------------------------------


 





