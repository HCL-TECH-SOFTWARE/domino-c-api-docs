




<!--
 /\* Font Definitions \*/
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




**Initial Release 5.0**



**Function : Mail Gateway**



**MailIsNotToBeHeld** **- Determine
whether a mail message is not to be held.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



BOOL
LNPUBLIC **MailIsNotToBeHeld(**  

      DHANDLE  hMessage**);**



**Description :**



This
function returns TRUE if the MAIL\_DONOTHOLD\_ITEM in the specified mail message
exists; returns FALSE otherwise.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  




Output :  

(routine)  -  TRUE if mail is not to be held, FALSE otherwise.  

  

  




 **See Also :**


**[MailOpenMessage](MailOpenMessage.md)**


**[MAIL\_xxx\_ITEM\_NUM(2)](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/9AB3CEDDDF02771B8525667A006D464F)**



----------------------------------------------------------------------------------------------------------


 





