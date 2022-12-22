




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




**Initial Release 7.0**



**Function : User Registration**



**REGNewServerExtended2** **- Registers
a new server.**


**----------------------------------------------------------------------------------------------------------**



**#include <reg.h>**



STATUS
LNPUBLIC **REGNewServerExtended2(**  

      HCERTIFIER  hCertCtx,  

      char far \*RegServer,  

      REG\_SERVER\_INFO far \*CertInfo,  

      REGSIGNALPROC  signalstatus,  

      char far \*retErrorPathName,  

      void far \*Spare**);**



**Description :**



This
function registers a new server.  


 


It performs
two functions, each of which is separately selectable by setting the
appropriate flag in the REGFlags member of REG\_SERVER\_INFO:  


(1) Create
and certify a server's ID file and 


(2) Add or
modify the server record in the Domino Directory on the registration server.  


 


It will open
the Domino Directory on the specified registration server, verifying write
access to the book, and look for the EntryName specified.  If the specified
server is found, an error will be returned unless the caller has specified that
the server entry may be modified.  If the ID file is found, an error will be
returned unless the caller has specified that it may be modified (overwritten).


 


**Parameters :**



Input :  

hCertCtx  -  Handle of a certifier context obtained by calling SECKFMGetCertifierCtx
(must be freed by a call to SECKFMFreeCertifierCtx).  

  

RegServer  -  A pointer to the null-terminated name of the Lotus Domino
registration server containing the Domino Directory.  The string should be no
longer than MAXUSERNAME. If you want to specify "no server" (the
local machine), pass a pointer to "" (the null string).  

  

CertInfo  -  A pointer to a REG\_SERVER\_INFO structure.  Please see
REG\_SERVER\_INFO.  

  

signalstatus  -  (Optional).  Pointer to a user defined procedure used to show status
during registration.  See Data Type, Signal Handler section of this reference. 
Otherwise use (REGSIGNALPROC) NULL for this parameter.  

  

Spare  -  Reserved for future use.  Use NULL.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  -  No error.  

  

ERR\_REG\_INC\_CONTEXT  -  Non-optional fields are incomplete.    

  

ERR\_REG\_ADDRBOOK\_ENTRY\_EXISTS  -  Flag not set to allow modification of
existing server record.  

  

ERR\_REG\_USERID\_EXISTS  -  Flag not set to allow overwriting of an existing
server id.  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  

retErrorPathName  -  (Optional).  Pathname of file where file system error
occurred.  

  




 **See Also :**


**[REG\_ID\_INFO](REG_ID_INFO.md)**


**[REG\_MISC\_INFO](REG_MISC_INFO.md)**


**[REG\_SERVER\_INFO](REG_SERVER_INFO.md)**



----------------------------------------------------------------------------------------------------------


 





