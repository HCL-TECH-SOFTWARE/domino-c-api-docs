




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




 


**Function : User Registration**



**SECKFMSetCertifierExpiration** **- Set the
certificate expiration date.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECKFMSetCertifierExpiration(**  

      HCERTIFIER  hKfmCertCtx,  

      TIMEDATE far \*pExpirationDate**);**



**Description :**



This function
sets the certificate expiration date for the entity that is being certified.


 


**Parameters :**



Input :  

hKfmCertCtx  -  Handle of a certifier context obtained from calling
SECKFMGetCertifierCtx (must be freed by a call to SECKFMFreeCertifierCtx).  

  

pExpirationDate  -  Pointer to the the certificate expiration date for the
entity that is being certified.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - action successful  

  

ERR\_xxx  -  Various OS, and KFM errors.  

  

  




 **See Also :**


**[REGNewCertifier](REGNewCertifier.md)**


**[REGNewWorkstation](REGNewWorkstation.md)**


**[SECKFMGetCertifierCtx](SECKFMGetCertifierCtx.md)**



----------------------------------------------------------------------------------------------------------


 





