




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



**REGNewWorkstation** **- Registers
a new workstation.**


**----------------------------------------------------------------------------------------------------------**



**#include <reg.h>**



STATUS
LNPUBLIC **REGNewWorkstation(**  

      HCERTIFIER  hCertCtx,  

      WORD  MakeIDType,  

      char far \*RegServer,  

      char far \*OrgUnit,  

      char far \*LastName,  

      char far \*FirstName,  

      char far \*MidInitial,  

      char far \*Password,  

      char far \*IDFileName,  

      char far \*Location,  

      char far \*Comment,  

      WORD  MailSystem,  

      char far \*MailServerName,  

      char far \*MailFileName,  

      char far \*ForwardAddress,  

      REGFlags  Flags,  

      WORD  MinPasswordLength,  

      REGSIGNALPROC  signalstatus,  

      char far \*ErrorPathName**);**



**Description :**



This
function registers a new workstation.  It performs three functions, each of
which can be selected separately by setting the appropriate flag in the REGFlags
word:  (1)  Create and certify a user's ID file; (2)  Create a mail file on the
user's specified mail server; and (3)  Add or modify the user's person record
in the Domino Directory on the registration server.  It will open the Domino
Directory on the specified registration server, verify write access to the
book, and look for the EntryName specified.  If the user is found, an error
will be returned unless the caller has specified in the REGFlags word that the
user entry may be modified.  If the ID file is found, an error will be returned
unless the caller has specified that it may be modified (overwritten).


 


**Parameters :**



Input :  

hCertCtx  -  Handle of a certifier context obtained by calling
SECKFMGetCertifierCtx (must be freed by a call to SECKFMFreeCertifierCtx).  You
may specify NULLHANDLE if you do not specify the fREGCreateIDFileNow and you do
specify a valid ID file for the IDFileName parameter.  

  

MakeIDType  -  Must be one of:  

KFM\_IDFILE\_TYPE\_FLAT --  Flat name space (V2 compatible)  

KFM\_IDFILE\_TYPE\_STD  --   Standard (user/server hierarchical)  

KFM\_IDFILE\_TYPE\_DERIVED -- Derived from certifier context (ie: 
non-hierarchical certifier context => FLAT, hierarchical certifier context
=>STD).  

  

RegServer  -  A pointer to the null-terminated name of the Lotus Domino
registration server containing the Domino Directory.  The string should be no
longer than MAXUSERNAME. If you want to specify "no server" (the
local machine), pass a pointer to "" (the null string).  

  

OrgUnit  -  (Optional).  Organizational unit of the new user (hierarchical only
and in addition to that derived from the certifier context).  

  

LastName  -  The last name of the new user (workstation).  

  

FirstName  -  (Optional).  The first name of the new user (workstation).  Do
not specify NULL for this parameter.  If no first name is to be used, specify,
"" (the null string), for this parameter.  

  

MidInitial  -  (Optional).  The middle initial of the new user (workstation).  

  

Password  -  (Optional).  The password for the new user (workstation).  

  

IDFileName  -  The pathname of the ID file for the new user (workstation).  If
the fREGCreateIDFileNow flag is not specified, then this file must exist in
order to create a mail file and/or add or modify the user's person record in
the Domino Directory.  Specify NULL for this parameter to have the IDFile
attached to the Person record in the Domino Directory (attached file name
defaults to UserID).  

  

Location  -  (Optional).  The location of the workstation (used to help in
identification if there is more than one with the same name).  Do not pass in a
literal constant.  

  

Comment  -  (Optional).  Any additional identifying information to be stored in
the Domino Directory.  

  

MailSystem  -  (Optional).  Defaults to Notes mail user.  One of:  

MAILSYSTEM\_NOTES - Notes mail user  

MAILSYSTEM\_CCMAIL - CC:mail user  

MAILSYSTEM\_VIMMAIL - VIM compatible mail user  

MAILSYSTEM\_NONE - no mail system  

  

MailServerName  -  (Optional).  Name of the server where the workstation's
mailfile will reside.  If you want to create the mailfile on the local system,
specify the user name associated with the workstation for this parameter.  Use
SECKFMGetUserName() to get the user name.  You must also specify the
fREGCreateMailFileNow in the flags parameter to create the mailfile.  

  

MailFileName  -  (Optional;  required if the flag fREGCreateMailFileNow is
specified).  The pathname of the mailfile.  

  

ForwardAddress  -  (Optional).  Another Notes domain or foreign mail gateway
where mail is to be forwarded.  

  

Flags  -  Flags that are set to specify options.  See Symbolic Value, fREGxxx,
in this reference.  

  

MinPasswordLength  -  Quality of password required for this user (0 - 16)  

  

signalstatus  -  (Optional).  Pointer to a user defined procedure used to show
status during registration.  See Data Type, Signal Handler section of this
reference.  Otherwise use (REGSIGNALPROC) NULL for this parameter.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  -  No error.  

ERR\_REG\_INC\_CONTEXT  -  Non-optional fields are incomplete.  Depends on Flags
used:  

     fREGCreateIDFileNow requires MakeIDType (defaults to DERIVED if invalid),
LastName, IDFileName, and Password (if MinPasswordLength is not 0).  

     fREGCreateMailFileNow requires LastName, MailServerName, and MailFileName.  

     fREGCreateAddrBookEntry requires LastName.  

ERR\_REG\_ADDRBOOK\_ENTRY\_EXISTS  -  Flag not set to allow modification of
existing user record.  

ERR\_REG\_USERID\_EXISTS  -  Flag not set to allow overwriting an existing user
id.  

ERR\_REG\_NO\_MAILFILE\_CREATED  -  Requested creation could not be done.  

ERR\_xxx  -  Various NSF, OS, and KFM errors.  

  

  

Location  -  Any run of white spaces in the input string will be replaced by a
single space.  

  

ErrorPathName  -  (Optional).  Pathname of file where file system error
occurred.  

  




 **Sample Usage :**


/\* Prepare to call
REGNewWorkstation() to create and register a new   

  user. First get the Organization Unit Certifier context for ABCorp,  

  Sales Unit. Then, pass this certifier context as input to   

  REGNewWorkstation(). It will certify the new user with this   

  certifier.   

\*/  

if (error = GetCertCtx(ORGUNIT\_CERT\_ID, &hCertCtx, "abcorp"))  

{  

    return (ERR(error));  

}  

     

error = REGNewWorkstation (  

      hCertCtx,              /\* certifier context \*/  

      KFM\_IDFILE\_TYPE\_DERIVED, /\* derived from certifier context \*/  

      ServName,              /\* Registration server \*/  

      "Inside Sales",        /\* Org Unit - provides uniqueness  

                                to the name \*/  

      "Doe",                 /\* Last name \*/  

      "Jayne",               /\* First name \*/  

      NULL,                  /\* no middle initial \*/  

      NULL,                  /\* no password initially \*/  

      USER\_ID,               /\* ID file name \*/  

      WorkLocation,          /\* location - optional \*/  

      NULL,                  /\* comment - optional \*/  

      MAILSYSTEM\_NOTES,             /\* mail system  \*/  

      ServName,              /\* mail server name \*/  

      MAILFILENAME,          /\* pathname of mail file \*/  

      NULL,                  /\* forward address - optional \*/  

      fREGCreateIDFileNow |  /\* flags \*/  

      fREGUSARequested    |  

      fREGCreateMailFileNow |  

      fREGCreateAddrBookEntry,  

      0,                      /\* minimum password length \*/  

      REGCallback,            /\* pointer to callback function \*/  

      FullDBPath);            /\* returned pathname of file where  

                                 error occurred \*/


 **See Also :**


**[SECKFMGetCertifierCtx](SECKFMGetCertifierCtx.md)**


**[SECKFMFreeCertifierCtx](SECKFMFreeCertifierCtx.md)**


**[REGSIGNALPROC](REGSIGNALPROC.md)**


**[fREGxxx](fREGxxx.md)**



----------------------------------------------------------------------------------------------------------


 





