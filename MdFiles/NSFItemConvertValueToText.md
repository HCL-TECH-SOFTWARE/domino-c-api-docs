




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



**NSFItemConvertValueToText** **- Given its
BLOCKID, convert item value to text.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



WORD
LNPUBLIC **NSFItemConvertValueToText(**  

      WORD  value\_type,  

      BLOCKID  value\_bid,  

      DWORD  value\_len,  

      char far \*text\_buf\_ptr,  

      WORD  text\_buf\_len,  

      char  separator**);**



**Description :**



This
function converts the value of an item to text where the item may be any one of
a variety of Domino data types. This function takes, as input, the data type
word, the BLOCKID of an item value, the length of that value (including the
WORD of Domino data type),  the address of the text buffer that will receive
the converted text, the length of that buffer,  and the single character that
will be used to separate multi-value items. This writes a zero-terminated
character text string to the specified text buffer and returns the length of
the text.  

  

Use this function to render an item value as printable text when you do not
have the handle to the open note that contains the item.  If the desired item
is already associated with a note, use the function NSFItemConvertToText, which
has a simpler argument list.  

  

The item value may be any one of the following Domino data types:   

  

TYPE\_TEXT - Text will be returned unmodified.  

TYPE\_TEXT\_LIST - A text list will be converted to text.  

TYPE\_USERID - The user name portion will be converted to text.  

TYPE\_NUMBER - the FLOAT/NUMBER type number will be converted to text.  

TYPE\_TIME - the binary time/date will be converted to text.


      TYPE\_COMPOSITE
- the composite item will be converted to text.  

TYPE\_ERROR - the binary Error value will be converted to "ERROR: ".  

TYPE\_UNAVAILABLE - the binary Unavailable value will be converted to
"UNAVAILABLE: ".  

  

The maximim size of the returned buffer is 60K.


 


**Parameters :**



Input :  

value\_type  -  A WORD containing the Domino data type of the item value.  

  

value\_bid  -  The BLOCKID of the item value you wish to convert into text.  

  

value\_len  -  A DWORD containing the length of the item value, including the
WORD of Domino data type.  

  

text\_buf\_len  -  A WORD containing the length of the text buffer.  

  

separator  -  A char value used to separate multiple values in the converted
text.  When converting a data type such as TYPE\_TEXT\_LIST, any character of
your choosing may be used.  If 0 is specified, then the default character value
';' (semicolon) will be used.  

  




Output :  

(routine)  -  Returns length of the converted text or zero if item was not
found.  

  

  

text\_buf\_ptr  -  The address of a text buffer in which the converted text and
the terminating '\0' (NULL) character are returned. The maximum size of the
buffer is 60K.  

  




 **Sample Usage :**


  

   /\* Get TEXT\_LIST\_ITEM from Note1, convert it to text and then \*/  

   /\*  add it to Note2  as TYPE\_TEXT                             \*/  

  

   if ( error\_status = NSFItemInfo(note1\_handle, TEXT\_LIST\_ITEM,  

                           strlen(TEXT\_LIST\_ITEM), &item\_bid,  

                           &value\_type, &value\_bid, &value\_len))  

       goto Exit;  

  

   NSFItemConvertValueToText(value\_type, value\_bid, value\_len,  

                           text\_buf1, LINEOTEXT-1, ',');  

  

   /\* Save Coverted Text List in Note2 as TEXT \*/  

  

   if (error\_status = NSFItemSetText(note2\_handle, CONV\_LIST\_ITEM,  

                          text\_buf1, (WORD) strlen(text\_buf1)))  

       goto Exit;


 **See Also :**


**[ConvertItemToText](ConvertItemToText.md)**


**[ConvertTIMEDATEToText](ConvertTIMEDATEToText.md)**


**[ConvertTIMEDATEPAIRToText](ConvertTIMEDATEPAIRToText.md)**


**[NSFItemConvertToText](NSFItemConvertToText.md)**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFItemInfoNext](NSFItemInfoNext.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**



----------------------------------------------------------------------------------------------------------


 





