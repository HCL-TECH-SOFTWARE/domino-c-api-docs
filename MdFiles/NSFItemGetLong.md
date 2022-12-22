




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



**NSFItemGetLong** **- Return
value of  TYPE\_NUMBER item as a LONG.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



LONG
LNPUBLIC **NSFItemGetLong(**  

      NOTEHANDLE  note\_handle,  

      const char far \*number\_item\_name,  

      LONG  number\_item\_default**);**



**Description :**



This
function takes a handle to an open note, the name for the item whose value you
wish to get and a default value to be returned by the function.


 


**Parameters :**



Input :  

note\_handle  -  A handle to an open note in memory.  

  

number\_item\_name  -  A pointer to a null-terminated item name.  

  

number\_item\_default  -  The default value to be returned by the function if the
item is not present.  

  




Output :  

(routine)  -  If TYPE\_NUMBER item is present, return the value coerced as a
LONG.  If item is not present, return the default value provided in the third
argrument.  

  

  




 **Sample Usage :**


/\* Print ULONG ITEM \*/  

  

   if (NSFItemIsPresent(note1\_handle,ULONG\_ITEM, strlen(ULONG\_ITEM)))  

       printf("%s: %lu\n", ULONG\_ITEM,  

              (NSFItemGetLong(note1\_handle, ULONG\_ITEM, 0L)));


 **See Also :**


**[NSFItemGetNumber](NSFItemGetNumber.md)**


**[NSFItemLongCompare](NSFItemLongCompare.md)**


**[NSFItemSetNumber](NSFItemSetNumber.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**



----------------------------------------------------------------------------------------------------------


 





