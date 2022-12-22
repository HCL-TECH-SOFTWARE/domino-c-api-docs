




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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



**REGNewCertifier** **- Creates
either an Organizational or Organizational Unit certifier.**


**----------------------------------------------------------------------------------------------------------**



**#include <reg.h>**



STATUS
LNPUBLIC **REGNewCertifier(**  

      HCERTIFIER  hCertCtx,  

      WORD  MakeIDType,  

      char far \*RegServer,  

      char far \*Country,  

      char far \*Org,  

      char far \*OrgUnit,  

      char far \*Password,  

      char far \*IDFileName,  

      char far \*Location,  

      char far \*Comment,  

      char far \*MailServerName,  

      char far \*MailFileName,  

      char far \*ForwardAddress,  

      REGFlags  Flags,  

      WORD  KeyWidth,  

      WORD  MinPasswordLength,  

      REGSIGNALPROC  signalstatus,  

      char far \*ErrorPathName**);**



**Description :**



This
function creates either an Organizational or Organizational Unit certifier.  It
performs three functions, each of which is separately selectable by setting the
appropriate flag in the REGFlags word:  (1) Create a certifier's ID file and
certify it if the certfier is of type ORGUNIT; (2) Create a mail file on the
certifier's specified mail server; and (3) Add or modify the certifier record
in the Domino Directory on the registration server.  It will open the Domino
Directory on the specified registration server, verify write access to the
book, and look for the certifier specified by Org or OrgUnit.  If the certifier
is found, an error will be returned unless the caller has specified in the
REGFlags word that the certifier record may be modified.  If the ID file is
found, an error will be returned unless the caller has specified that it may be
modified (overwritten).


 


**Parameters :**



Input :  

hCertCtx  -  Handle of a certifier context obtained from calling
SECKFMGetCertifierCtx (must be freed by a call to SECKFMFreeCertifierCtx).  Use
NULLHANDLE if creating an Organizational certifier.  

  

MakeIDType  -  One of:  

     KFM\_IDFILE\_TYPE\_ORG - Organizational certifier.  

            The Org name is required, a Country is optional.  OrgUnit must be
NULL.  

     KFM\_IDFILE\_TYPE\_ORGUNIT - Organizational unit certifier.  

            The OrgUnit is required.  Org and Country must be NULL.  

       KFM\_IDFILE\_TYPE\_INET - Internet certifier.  No ID file is created.  

  

RegServer  -  A pointer to the null-terminated name of the Lotus Domino
registration server containing the Domino Directory.  The string should be no
longer than MAXUSERNAME. If you want to specify "no server" (the
local machine), pass a pointer to "" (the null string).  

  

Country  -  (Optional).  Country code of certifier.  

  

Org  -  Organization of the new certifier if of type ORG.  

  

OrgUnit  -  Organization unit of the new certifier if of type ORGUNIT.  

  

Password  -  (Optional).  The password for the new certifier.  

  

IDFileName  -  The pathname of the ID file for the new certifier.   If the
fREGCreateIDFileNow flag is not specified, then this file must exist in order
to create a mail file and/or add or modify the certifier record in the Domino
Directory.  

  

Location  -  (Optional).  The location of the certifier.  Do not pass in a
literal constant.  

  

Comment  -  (Optional).  Any additional identifying information to be stored in
the Domino Directory.  

  

MailServerName  -  (Optional).  Name of mail server where the mail file is to
be created.  If the flag fREGCreateMailFileNow is specified and no mail server
name is supplied (the pointer is NULL), the mail file will be created on the
local system.  

  

MailFileName  -  (Optional;  required if the flag fREGCreateMailFileNow is
specified).  Name of the mail file to create.  

  

ForwardAddress  -  (Optional).  Another Notes domain or foreign mail gateway
where mail is to be forwarded.  

  

Flags  -  Flags that are set to specify options.  See Symbolic Value, fREGxxx,
in this reference.  

  

KeyWidth  -  (Reserved for future use).  Must be 0.  

  

MinPasswordLength  -  Quality of password required for this certifier (0 - 16).  

  

signalstatus  -  (Optional).  Pointer to a user defined procedure used to show
status during registration.  See Data Type, Signal Handler section of this
reference.  Otherwise use (REGSIGNALPROC) NULL for this parameter.  

  




Output :  

(routine)  -  Return status from this call - indicates either success or what
the error is.  The return codes include:  

  

NOERROR  -  No error.  

ERR\_REG\_INC\_CONTEXT  -  Non-optional fields are incomplete.  Depends on Flags
used:  

     fREGCreateIDFileNow requires hCertCtx if type is ORGUNIT, valid MakeIDType
(defaults to ORG if invalid), Org (if type ORG), OrgUnit (if type ORGUNIT),
IDFileName, and Password (if MinPasswordLength is not 0).  

     fREGCreateAddrBookEntry requires Org (if type ORG), and OrgUnit (if type
ORGUNIT).  

ERR\_REG\_ADDRBOOK\_ENTRY\_EXISTS  -  Flag not set to allow modification of
existing certifier record.  

ERR\_REG\_USERID\_EXISTS  -  Flag not set to allow overwriting of an existing id.  

ERR\_xxx  -  Various NSF, OS, and KFM errors.  

  

  

Location  -  Any run of white spaces in the input string will be replaced by a
single space.  

  

ErrorPathName  -  (Optional).  Pathname of file where file system error
occurred.  

  




 **Sample Usage :**


/\* Prepare to call
REGNewCertifier to create and register a new   

  organizational unit certifier - Sales org unit of ABCorp.   

  First get the Organization Certifier context for ABCorp, then pass  

  this context as input to REGNewCertifier.   

\*/  

  

if (error = GetCertCtx(ORG\_CERT\_ID, &hCertCtx, "abcorp"))  

{  

   return (ERR(error));  

}  

     

error = REGNewCertifier (  

           hCertCtx,              /\* certifier context \*/  

           KFM\_IDFILE\_TYPE\_ORGUNIT, /\* Organizational Unit certifier \*/  

           ServName,              /\* registration server \*/  

           NULL,                  /\* country code - optional\*/  

           NULL,                  /\* Organization - Just use the above  

                                     certifier context \*/  

           ORGUNIT\_CERTNAME,      /\* Org Unit \*/  

           "abcorp",              /\* password \*/  

           ORGUNIT\_CERT\_ID,       /\* ID file for new certifier \*/  

           NULL,                  /\* location of certifier - optional \*/  

           NULL,                  /\* comment - optional \*/  

           NULL,                  /\* Mail Server's name - optional \*/  

           NULL,                  /\* Mail file's name - optional \*/  

           DNAME\_JAYNE,           /\* forwarding address \*/  

           fREGCreateIDFileNow |  /\* flags \*/  

           fREGUSARequested    |  

           fREGCreateAddrBookEntry,  

           0,                      /\* key width (must be 0) \*/  

           MIN\_PASS\_LEN,           /\* minimum password length \*/  

           REGCallback,            /\* pointer to callback function \*/  

           FullDBPath);            /\* returned pathname of file where  

                                      error occurred \*/


 **See Also :**


**[SECKFMGetCertifierCtx](SECKFMGetCertifierCtx.md)**


**[SECKFMFreeCertifierCtx](SECKFMFreeCertifierCtx.md)**


**[REGSIGNALPROC](REGSIGNALPROC.md)**



----------------------------------------------------------------------------------------------------------


 





