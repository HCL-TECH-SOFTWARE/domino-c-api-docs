




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




**Initial Release 6**



**Function : Address Book**



**SECNABRemoveCertificate** **- Remove
certificate from an open note.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECNABRemoveCertificate(**  

      NOTEHANDLE  hNote,  

      void \*pCertificate,  

      DWORD  CertificateSize,  

      DWORD  ReservedFlags,  

      void \*pReserved**);**



**Description :**



Remove
certificate from an open note.


 


**Parameters :**



Input :  

hNote  -  Handle to the open note to remove the certificate from.  

  

pCertificate  -  Pointer to the certificate to be removed from the list of
certificates in the field name of the open note.  

  

CertificateSize  -  Size of certificate to be removed.  

  

ReservedFlags  -  Reserved, should be set to zero.  

  

pReserved  -  Reserved, should be set to NULL.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Certificate successfully removed.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.   

  

  




 **See Also :**


**[SECNABAddCertificate](SECNABAddCertificate.md)**


**[SECNABEnumerateCertificates](SECNABEnumerateCertificates.md)**



----------------------------------------------------------------------------------------------------------


 





