




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



**NSFItemGetNumber** **- Get the
value of  TYPE\_NUMBER Item.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



BOOL
LNPUBLIC **NSFItemGetNumber(**  

      NOTEHANDLE  hNote,  

      const char far \*ItemName,  

      NUMBER far \*retNumber**);**



**Description :**



This function
takes a handle to an open note and the name for the Item whose value you wish
to get.  It returns the Item's value in a FLOAT variable.


 


**Parameters :**



Input :  

hNote  -  A handle to an open note in memory.  

  

ItemName  -  A pointer to a null-terminated item name.  

  




Output :  

(routine)  -  TRUE - If Item was present and successfully retrieved.  FALSE  -
if Item was not present.  

  

  

retNumber  -  The address of a NUMBER (or equivalent 'double') variable in
which the floating point number retrieved from named Item in the open note will
be returned.  

  




 **Sample Usage :**


/\* Print FLOAT ITEM \*/  

  

double num;  

if (NSFItemGetNumber (note1\_handle, FLOAT\_ITEM, &num))  

  printf("%s: %le\n", FLOAT\_ITEM, num);


 **See Also :**


**[NSFItemGetLong](NSFItemGetLong.md)**


**[NSFItemLongCompare](NSFItemLongCompare.md)**


**[NSFItemSetNumber](NSFItemSetNumber.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**



----------------------------------------------------------------------------------------------------------


 





