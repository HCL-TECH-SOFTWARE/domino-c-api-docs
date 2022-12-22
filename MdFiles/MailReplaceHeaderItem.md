




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



**MailReplaceHeaderItem** **- Adds a
header item to an open message.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailReplaceHeaderItem(**  

      DHANDLE  hMessage,  

      WORD  ItemCode,  

      const void far \*Value,  

      WORD  ValueLength**);**



**Description :**



This
function adds a header item to an open message.  Any previous item of the same
name is first deleted.  The item is added by passing a pointer to the item
value.  

  

This function always sets the ITEM\_SUMMARY item flag, allowing the item to be
used in views and formulas.  However, if the item value is greater than 8KB,
NSF clears the ITEM\_SUMMARY flag.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  

ItemCode  -  Item code; all of the MAIL\_xxx\_ITEM\_NUM item codes are valid.  

  

Value  -  Item value pointer.  

  

ValueLength  -  Item value length.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **See Also :**


**[MAIL\_xxx\_ITEM\_NUM(1)](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255CF1005E1A42)**


**[MAIL\_xxx\_ITEM\_NUM(2)](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/9AB3CEDDDF02771B8525667A006D464F)**



----------------------------------------------------------------------------------------------------------


 





