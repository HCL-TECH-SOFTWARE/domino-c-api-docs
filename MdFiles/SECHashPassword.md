




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




**Initial Release 5.0.11**



**Function : User Registration**



**SECHashPassword** **- Returns
the more secure digest, given an unencoded password.** 


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **SECHashPassword(**  

      WORD  wPasswordLen,  

      BYTE \*Password,  

      WORD  wMaxDigestLen,  

      WORD \*retDigestLen,  

      BYTE \*retDigest,  

      DWORD  ReservedFlags,  

      void \*pReserved**);**



**Description :**



This
function takes an unencoded password and returns the more secure version of the
digest. The Internet Password is in this "more secure" format.


 


**Parameters :**



Input :  

wPasswordLen  -  Length of an unencoded password to be digested.  

  

Password  -  An unencoded password to be digested  

  

wMaxDigestLen  -  Maximum output length of retDigest  

  

ReservedFlags  -  Should be set to 0. Reserved.  

  

pReserved  -  Should be set to NULL. Reserved.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retDigestLen  -  Length of digest that is returned   

  

retDigest  -  Digest that is returned   

  




 **See Also :**


**[SECVerifyPassword](SECVerifyPassword.md)**



----------------------------------------------------------------------------------------------------------


 





