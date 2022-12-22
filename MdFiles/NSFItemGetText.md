




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



**NSFItemGetText** **- Get the
value of  a TYPE\_TEXT item.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



WORD
LNPUBLIC **NSFItemGetText(**  

      NOTEHANDLE  note\_handle,  

      const char far \*item\_name,  

      char far \*item\_text,  

      WORD  text\_len**);**



**Description :**



This
function takes a handle to an open note and the name of a text item whose value
you wish to get.  The function copies the text item into a buffer provided by
you, and returns the length of the text that was retrieved.   

If the buffer is smaller than the text item, the text item will be truncated
and the returned length will be the length of the truncated item.  

  

The retrieved text may contain embedded null ('\0') characters. Notes uses null
characters (a char with value zero) to designate newlines. You must convert the
null characters to the appropriate newline character for your system before
printing out the retrieved text.  

  

NOTE: This function does not distinguish between an item with zero length and
an item that does not exist. In both cases, NSFItemGetText returns a length of
zero. You may use NSFItemIsPresent to see if an item exists.


 


**Parameters :**



Input :  

note\_handle  -  A handle to an open note.  

  

item\_name  -  A pointer to a null-terminated item name.  

  

text\_len  -  A WORD containing the length of the text buffer.   

  




Output :  

(routine)  -  Length of the text that was retrieved.  

  

  

item\_text  -  The address of a text buffer in which the item's contents will be
returned.  

  




 **Sample Usage :**


field\_len =
NSFItemGetText (   

                hNote,   

                ITEM\_NAME\_CATEGORIES,  

                field\_text,  

                sizeof (field\_text));


 **See Also :**


**[NSFItemSetText](NSFItemSetText.md)**


**[NSFItemTextEqual](NSFItemTextEqual.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[NSFItemInfo](NSFItemInfo.md)**



----------------------------------------------------------------------------------------------------------


 





