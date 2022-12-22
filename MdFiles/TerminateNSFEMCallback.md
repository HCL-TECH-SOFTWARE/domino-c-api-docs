




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



**Function : Extension Manager**



**TerminateNSFEMCallback** **- Extension
Manager callback for EM\_TERMINATENSF**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



void
LNPUBLIC **TerminateNSFEMCallback(**  

      void \*unused\_params**);**



**Description :**



EM\_TERMINATENSF
occurs when NSF service terminates for the process, right before the extension
manager DLLs are unloaded.  


 


Do not
de-register callback functions in the callback routine for the EM\_TERMINATENSF
notification.


 


**Parameters :**



Input :  

unused\_params  -  Reserved for future use.  

  




 


 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





