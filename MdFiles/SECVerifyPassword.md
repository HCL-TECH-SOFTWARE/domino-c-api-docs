




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



**SECVerifyPassword** **- Verifies
an unencoded password against a digest password value.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **SECVerifyPassword(**  

      WORD  wPasswordLen,  

      BYTE \*Password,  

      WORD  wDigestLen,  

      BYTE \*Digest,  

      DWORD  ReservedFlags,  

      void \*pReserved**);**



**Description :**



This
function verifies an unencoded password against a digest password value. The
unencoded password can be either an unencoded Internet Password or Notes ID
Password. The digest password value can be either an Internet Password (more
secure digest value) or a Password Digest. The unencoded Internet Password is
verified against the Internet Password. The Notes ID Password is verified
against the Password Digest. 


 


**Parameters :**



Input :  

wPasswordLen  -  Length of unencoded password to be verified.  

  

Password  -  Unencoded password to be verified.  

  

wDigestLen  -  Length of digest to be compared against.  

  

Digest  -  Digest to be compared against.  

  

ReservedFlags  -  Should be set to 0. Reserved.  

  

pReserved  -  Should be set to NULL. Reserved.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success (the
values compare) or what the error is. The return codes include:  

  

NOERROR -  The values compare   

ERR\_SECURE\_BADPASSWORD - Not verified (values do not compare)  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **See Also :**


**[SECHashPassword](SECHashPassword.md)**



----------------------------------------------------------------------------------------------------------


 





