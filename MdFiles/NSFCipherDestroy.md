




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




**Initial Release 8.0.1**



**Function : encryption**



**NSFCipherDestroy** **- Destroy a
CIPHERHANDLE**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFCipherDestroy(**  

      CIPHERHANDLE \*phCipher**);**



**Description :**



Destroy a
CIPHERHANDLE that was returned as an output argument from another NSF
function.  Returns NOERROR if phCipher is NULL or \*phCipher is      NULLCIPHERHANDLE.


 


**Parameters :**



Input :  

phCipher  -  Handle for a cryptographic operation  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successful.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  




 




----------------------------------------------------------------------------------------------------------


 





