




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



**SECNABEnumerateCertificates** **- Enumerate
certificates found in an open note.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECNABEnumerateCertificates(**  

      NOTEHANDLE  hNote,  

      SECNABENUMPROC  CallBack,  

      void \*pCallCtx,  

      DWORD  ReservedFlags,  

      void \*pReserved**);**



**Description :**



For the open
note specified, this function looks for certificates in the field name and
calls a callback function for each certificate found.


 


**Parameters :**



Input :  

hNote  -  Handle to the open note to be enumerated.  

  

CallBack  -  Callback function to be executed for each certificate found in the
field name.   If the return from this user callback is TRUE, then
SECNABEnumerateCertificates stops calling this routine.  

  

pCallCtx  -  Caller's context to be passed into the CallBack function.  This
user defined context can be used to store the certificate information gathered
in the CallBack function.  

  

ReservedFlags  -  Reserved, must be zero.  

  

pReserved  -  Reserved.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - action successful  

  

  




 **See Also :**


**[SECNABAddCertificate](SECNABAddCertificate.md)**


**[SECNABENUMPROC](SECNABENUMPROC.md)**


**[SECNABRemoveCertificate](SECNABRemoveCertificate.md)**



----------------------------------------------------------------------------------------------------------


 





