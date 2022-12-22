




<!--
 /\* Font Definitions \*/
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



**MailGetMessageItemHandle** **- Returns a
handle to the value for a message header item.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailGetMessageItemHandle(**  

      DHANDLE  hMessage,  

      WORD  ItemCode,  

      BLOCKID far \*retbhValue,  

      WORD far \*retValueType,  

      DWORD far \*retValueLength**);**



**Description :**



This
function returns a handle ("block ID" or pool handle and offset) to
the value for a specified message header item.  The item can be of any data
type.  The caller can use the OS Pool functions to obtain a pointer to the
value of the item.  

  

The BLOCKID value obtained using this function refers to memory within a note. 
This memory is managed by Domino, and should not be freed by the application.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  

ItemCode  -  Item code; all of the MAIL\_xxx\_ITEM\_NUM codes are valid.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

retbhValue  -  Item value handle.  

  

retValueType  -  Item value data type (TYPE\_xxx).  

  

retValueLength  -  Item value length in bytes.  

  




 **See Also :**


**[MailGetMessageItem](MailGetMessageItem.md)**


**[MAIL\_xxx\_ITEM\_NUM(1)](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255CF1005E1A42)**


**[MAIL\_xxx\_ITEM\_NUM(2)](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/9AB3CEDDDF02771B8525667A006D464F)**



----------------------------------------------------------------------------------------------------------


 





