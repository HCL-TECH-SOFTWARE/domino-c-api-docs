




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



**NSFItemLongCompare** **- Compare
(long) item to a given (long) value.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



BOOL
LNPUBLIC **NSFItemLongCompare(**  

      NOTEHANDLE  note\_handle,  

      const char far \*item\_name,  

      long  long \_value,  

      int far \*result\_ptr**);**



**Description :**



This
function takes a handle to an open note, the name for the TYPE\_NUMBER Item
whose value you wish to compare,  the (long) value to be used in the
comparison.  It returns a int whose value indicates the result of the
comparison: -1 if item (long) is greater, 0 if they are equal, and 1 if item
(long) is less.


 


**Parameters :**



Input :  

note\_handle  -  A handle to an open note in memory.  

  

item\_name  -  The address of a null-terminated Item name.  

  

long \_value  -  A (long) value you wish to compare with a NUMBER item in the
open note.  All values of  TYPE\_NUMBER are stored in IEEE floating point
format, so the NUMBER item is first coerced into a (long), and then that value
(minus the decimal fraction) is used in the comparison.  

  




Output :  

(routine)  -  Always returns FALSE.  

  

  

result\_ptr  -  The address of the int containing outcome of the comparison: -1
means the NUMBER item is larger, 0 means they are equal, and 1 means the NUMBER
item is smaller.  

  




 **Sample Usage :**


/\* Compare  ULONG in
Note to another value \*/  

  

ulong\_num2 = 3430000L;  

printf("Is ULONG in Note equal to %lu ?\n", ulong\_num2);  

if (NSFItemIsPresent(note1\_handle, ULONG\_ITEM,strlen(ULONG\_ITEM)))  

{  

   NSFItemLongCompare(note1\_handle, ULONG\_ITEM,  

                          (long) ulong\_num2, &answer);  

   if (answer == 0)  

      printf("Answer: %s\n", "YES YES YES!");  

   else if(answer != 0)  

      printf("Answer: %s\n", "Nooooooooo!");  

}


 **See Also :**


**[NSFItemGetLong](NSFItemGetLong.md)**


**[NSFItemGetNumber](NSFItemGetNumber.md)**


**[NSFItemSetNumber](NSFItemSetNumber.md)**


**[NSFItemTextEqual](NSFItemTextEqual.md)**


**[NSFItemTimeCompare](NSFItemTimeCompare.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**



----------------------------------------------------------------------------------------------------------


 





