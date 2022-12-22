




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



**NSFItemGetTextListEntries** **- Return
number of entries in TYPE\_TEXT\_LIST item.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



WORD
LNPUBLIC **NSFItemGetTextListEntries(**  

      NOTEHANDLE  note\_handle,  

      const char far \*item\_name**);**



**Description :**



This
function takes a handle to an open note and the name for the text list Item
from which to  obtain the number of text list entries. The function returns the
number of entries in the text list item.


 


**Parameters :**



Input :  

note\_handle  -  A handle to an open note in memory.  

  

item\_name  -  A pointer to a null-terminated Item name.  

  




Output :  

(routine)  -  Return the number of entries in the text list.  

  

  




 **Sample Usage :**


/\* Print the
TEXT\_LIST\_ITEM \*/  

  

num\_entries = NSFItemGetTextListEntries(note1\_handle,  

                                           TEXT\_LIST\_ITEM);  

for (counter = 0; counter < num\_entries; counter++)  

{  

   text\_len = NSFItemGetTextListEntry(note1\_handle,  

                    TEXT\_LIST\_ITEM, counter, text\_buf2, LINEOTEXT-1);  

   text\_buf2[text\_len] = '\0';  

   printf("%s[%u]: %s\n", TEXT\_LIST\_ITEM, counter, text\_buf2);  

}


 **See Also :**


**[NSFItemAppendTextList](NSFItemAppendTextList.md)**


**[NSFItemCreateTextList](NSFItemCreateTextList.md)**


**[NSFItemGetTextListEntry](NSFItemGetTextListEntry.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[ListGetNumEntries](ListGetNumEntries.md)**



----------------------------------------------------------------------------------------------------------


 





