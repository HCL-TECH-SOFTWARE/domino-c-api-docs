




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




 


**Function : Mail Gateway**



**MailGetMessageItem** **- Returns
the value of a text header item.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailGetMessageItem(**  

      DHANDLE  hMessage,  

      WORD  ItemCode,  

      char far \*retString,  

      WORD  StringSize,  

      WORD far \*retStringLength**);**



**Description :**



This
function returns the value of a text header item.  

  

If the item text is larger than the buffer size, the returned string is
truncated.  

  

If the item is a text list, a concatenation of the values in a text list (with
commas as delimiters) is returned.  

  

If the item is not a text or text list item, a zero-length string is returned.  

  

This function should generally only be used for items that are known to be
relatively small (less than 1KB), since it requires a fixed length buffer.  The
MailGetMessageItemHandle should typically be used for text lists and items that
can be large since it returns a pointer to the item instead of copying, as
MailGetMessageItem does.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  

ItemCode  -  Item code (MAIL\_xxx\_ITEM\_NUM).  

  

StringSize  -  Text string buffer size.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

retString  -  Text string value (null-terminated).  

  

retStringLength  -  Text string length (not including '\0').  

  




 **Sample Usage :**


char        String[MAXSPRINTF+1];  

WORD        StringLength;  

  

  

/\* From \*/  

MailGetMessageItem (hMessage, MAIL\_FROM\_ITEM\_NUM, String,   

                                MAXSPRINTF, &StringLength);  

String[StringLength] = '\0';  

printf ("\tFrom: %s\n", String);


 **See Also :**


**[MailGetMessageItemHandle](MailGetMessageItemHandle.md)**


**[MAIL\_xxx\_ITEM\_NUM(1)](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255CF1005E1A42)**


**[MAIL\_xxx\_ITEM\_NUM(2)](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/9AB3CEDDDF02771B8525667A006D464F)**



----------------------------------------------------------------------------------------------------------


 





