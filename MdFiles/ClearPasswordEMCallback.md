




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




**Initial Release 4.0**



**Function : Extension Manager**



**ClearPasswordEMCallback** **- Extension
Manager callback for EM\_CLEARPASSWORD**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



STATUS
LNPUBLIC **ClearPasswordEMCallback(**void**);**



**Description :**



EM\_CLEARPASSWORD
occurs when a password is to be "cleared" either due to a timeout or
because the user has pressed F5.  EM\_CLEARPASSWORD can only be registered with
the EM\_REG\_BEFORE flag.  An extension manager hook for EM\_CLEARPASSWORD cannot
be called after Domino or Notes processes this operation.


 


**Parameters :**




Output :  

(routine)  -    

ERR\_EM\_CONTINUE  

  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





