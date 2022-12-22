




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



**NSFItemConvertToText** **- Given an
item name, convert its value to text.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



WORD
LNPUBLIC **NSFItemConvertToText(**  

      NOTEHANDLE  note\_handle,  

      const char far \*item\_name\_ptr,  

      char far \*text\_buf\_ptr,  

      WORD  text\_buf\_len,  

      char  separator**);**



**Description :**



This is a
very powerful function that converts many kinds of Domino fields (items) into
text strings. The function takes a handle to an open note, the name of an
item,  the address of the text buffer that will receive the text, the length of
that buffer, and the character that will be used to separate multiple values in
a field.  

  

If there is more than one item with the same name, this function will always
return the first of these. This function, therefore, is not useful if you want
to retrieve multiple instances of the same field name. For these situations,
use NSFItemConvertValueToText.  

  

The item value may be any one of these supported Domino data types:   

  

TYPE\_TEXT - Text is returned unmodified.  

  

TYPE\_TEXT\_LIST - A text list items will merged into a single text string, with
the separator between them.  

  

TYPE\_NUMBER - the FLOAT number will be converted to text.  

  

TYPE\_NUMBER\_RANGE -- the FLOAT numbers will be converted to text, with the
separator between them.  

  

TYPE\_TIME - the binary Time/Date will be converted to text.  

  

TYPE\_TIME\_RANGE -- the binary Time/Date values will be converted to text, with
the separator between them.  

  

TYPE\_COMPOSITE - The text portion of the rich text field will be returned.  

  

TYPE\_USERID - The user name portion will be converted to text.  

  

TYPE\_ERROR - the binary Error value will be converted to "ERROR: ".  

  

TYPE\_UNAVAILABLE - the binary Unavailable value will be converted to
"UNAVAILABLE: ".  

  




 


**Parameters :**



Input :  

note\_handle  -  A NOTEHANDLE to the open note containing item you wish to
convert.  

  

item\_name\_ptr  -  The address of a null-terminated LMBCS string containing the
name of the item you wish to convert.  

  

text\_buf\_len  -  A WORD containing the length of the text buffer. The maximum
buffer size allowed is 60K.   

  

separator  -  A char value used to separate multiple values in the converted
text.  When converting a data type such as TYPE\_TEXT\_LIST, any character of
your choosing may be used.  If 0 is specified, then the default character value
';' (semicolon) will be used.  

  




Output :  

(routine)  -  Returns length of the converted text or zero if item was not
found.  

  

  

text\_buf\_ptr  -  The address of a text buffer in which the converted text and
the terminating '\0' (NULL) character are returned. The maximum buffer size
allowed is 60K.  

  




 **Sample Usage :**


  

   /\* Convert TIMEDATE in Note1 to text and add it to Note2 \*/  

  

    NSFItemConvertToText(note1\_handle, TIME\_ITEM, text\_buf2,  

                         sizeof(text\_buf2), ';');  

  

   /\* Save coverted time in Note2 as TEXT \*/  

  

   if (error\_status = NSFItemSetText(note2\_handle,  

                          CONV\_TIME\_ITEM, text\_buf2,  

                          (WORD) strlen(text\_buf2)))  

       goto Exit;  

  




 **See Also :**


**[ConvertItemToText](ConvertItemToText.md)**


**[ConvertTIMEDATEPAIRToText](ConvertTIMEDATEPAIRToText.md)**


**[ConvertTIMEDATEToText](ConvertTIMEDATEToText.md)**


**[NSFItemConvertToText](NSFItemConvertToText.md)**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFItemInfoNext](NSFItemInfoNext.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**



----------------------------------------------------------------------------------------------------------


 





