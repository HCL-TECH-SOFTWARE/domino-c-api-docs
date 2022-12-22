




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




**Initial Release 5.0.3**



**Function : IDs**



**PKCS12\_ImportFileToIDFile** **- Insert
the certificates and keys from a PKCS 12 file into an ID file.**


**----------------------------------------------------------------------------------------------------------**



**#include <pkcs12.h>**



STATUS
LNPUBLIC **PKCS12\_ImportFileToIDFile(**  

      char \*pPKCS12Filename,  

      char \*pPKCS12Filepassword,  

      char \*pIdFilename,  

      char \*pIdFilepassword,  

      DWORD  ImportFlags,  

      DWORD  ReservedFlags,  

      void \*pReserved**);**



**Description :**



Insert the
certificates and keys from a Public Key Cryptography Standards
#12  file into an ID file.  This function is supported for Windows 32-bit, IBM
AIX and Macintosh platforms only. 


 


**Parameters :**



Input :  

pPKCS12Filename  -  Pointer of the name of the PKCS 12 file to be parsed.  

  

pPKCS12Filepassword  -  Pointer to PKCS 12 file password.  

  

pIdFilename  -  Pointer to the name of an ID file which the keys and the
certificates will be inserted into.  

  

pIdFilepassword  -  Pointer to the password of the ID file which the keys and
the certificates will be inserted into.  

  

ImportFlags  -  0 or one of the values specified in PKCS12\_xxx.  

  

ReservedFlags  -  Reserved for future expansion.  Should be set to 0.  

  

pReserved  -  Reserved for future expansion.  Should be set to NULL.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **See Also :**


**[PKCS12\_ExportIDFileToFile](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6333C7EBD2C037AB852568AB0053536C)**


**[PKCS12\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CAEB39F00D3E5EB4852568AB0053536A)**



----------------------------------------------------------------------------------------------------------


 





