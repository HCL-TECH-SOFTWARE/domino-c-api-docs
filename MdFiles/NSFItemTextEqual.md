




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



**NSFItemTextEqual** **- Test if
item text is equal to a given text string.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



BOOL
LNPUBLIC **NSFItemTextEqual(**  

      NOTEHANDLE  note\_handle,  

      const char far \*item\_name,  

      const char far \*item\_text,  

      WORD  text\_len,  

      BOOL  case\_sensitive\_flag**);**



**Description :**



This
function takes a handle to an open note, the name for the TYPE\_TEXT Item whose
value you wish to test,  the test text, the length of that text, and a boolean
value indicating whether or not to ignore case during the comparison..  It
returns TRUE if the text is equal or FALSE if it is not.


 


**Parameters :**



Input :  

note\_handle  -  A handle to an open note in memory.  

  

item\_name  -  The address of a null-terminated string containing the Item name.  

  

item\_text  -  The address of the text buffer containing the test text.  

  

text\_len  -  A WORD containing the length of the test text buffer.  If the
length MAXWORD is used, then the string is assumed to be null-terminated, and
the length of the null-terminated string is used instead.  

  

case\_sensitive\_flag  -  A BOOL containing:  TRUE to consider case or FALSE to
ignore case during the comparison.  

  




Output :  

(routine)  -  Returns: TRUE if text strings are equal.  FALSE if they are NOT
equal.  

  

  




 **Sample Usage :**


/\* Compare text to text
item ignoring case! \*/  

  

printf("Does %s: %s\nEqual %s: %s if case is ignored ?\n",  

           TEXT\_ITEM, text\_buf1,  

           TEXT\_ITEM, SOME\_TEXT3);  

printf("Answer: %s\n", (NSFItemTextEqual(note1\_handle, TEXT\_ITEM,  

                              SOME\_TEXT3, strlen(SOME\_TEXT3),FALSE))  

                              ? "YES YES YES!" :
"Nooooooooo!");


 **See Also :**


**[NSFItemLongCompare](NSFItemLongCompare.md)**


**[NSFItemSetText](NSFItemSetText.md)**


**[NSFItemTimeCompare](NSFItemTimeCompare.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**



----------------------------------------------------------------------------------------------------------


 





