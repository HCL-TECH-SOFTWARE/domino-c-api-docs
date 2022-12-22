




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



**NSFItemTimeCompare** **- Compare
TYPE\_TIME item value to a TIMEDATE.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



BOOL
LNPUBLIC **NSFItemTimeCompare(**  

      NOTEHANDLE  note\_handle,  

      const char far \*item\_name,  

      const TIMEDATE far \*td\_item\_ptr,  

      int far \*result\_ptr**);**



**Description :**



This
function takes a handle to an open note, the name for the TYPE\_TIME Item whose
value you wish to compare,  the TIMEDATE value to be used in the comparison. 
It returns a value that indicates the result of the comparison: -1 means the
specified TIMEDATE value to be used in the comparison is older,  0 means they
are equal, and 1 means the specified TIMEDATE value to be used in the
comparison is later.


 


**Parameters :**



Input :  

note\_handle  -  A handle to an open note in memory.  

  

item\_name  -  The address of a null-terminated item name.  

  

td\_item\_ptr  -  The address of a TIMEDATE variable containing the TIMEDATE
value to be used in the comparison.  If NULL is provided, then the current
system Time/Date will be used for the comparison.  If a pointer to a
TIMEDATE\_PAIR is provided, then the comparison will be made using the first
member of the that structure.  

  




Output :  

(routine)  -  Returns TRUE if the comparison was successfully done; returns
FALSE if the item was not found or if the item is not of TYPE\_TIME.  

  

  

result\_ptr  -  The address of the int containing outcome of the comparison: -1
means the td\_item\_ptr TIMEDATE is older, 0 means they are the same, and 1 means
the td\_item\_ptr TIMEDATE is later.  

  




 **Sample Usage :**


/\* Compare time in Note
to current time \*/  

  

OSCurrentTIMEDATE(&current\_td);  

printf("Can TIMEDATE in Note be equal to current TIMEDATE?\n");  

if (NSFItemIsPresent(note1\_handle, TIME\_ITEM, strlen(TIME\_ITEM)))  

{  

   NSFItemTimeCompare(note1\_handle, TIME\_ITEM,  

                         &current\_td, &answer);  

   if (answer == 0)  

      printf("Answer: %s\n", "YES YES YES!");  

   else if(answer != 0)  

      printf("Answer: %s\n", "Nooooooooo!");  

}


 **See Also :**


**[NSFItemGetTime](NSFItemGetTime.md)**


**[NSFItemLongCompare](NSFItemLongCompare.md)**


**[NSFItemSetTime](NSFItemSetTime.md)**


**[NSFItemTextEqual](NSFItemTextEqual.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**



----------------------------------------------------------------------------------------------------------


 





