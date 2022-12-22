




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




**Initial Release 5.0**



**Function : User Registration**



**REGNewUser** **- Registers
a new workstation.**


**----------------------------------------------------------------------------------------------------------**



**#include <reg.h>**



STATUS
LNPUBLIC **REGNewUser(**  

      HCERTIFIER  hCertCtx,  

      WORD  MakeIDType,  

      char far \*RegServer,  

      REG\_USERNAME\_INFO far \*RegUserNameInfo,  

      REG\_MAIL\_INFO far \*RegMailInfo,  

      char far \*Password,  

      void far \*pGroupList,  

      char far \*IDFileName,  

      char far \*Location,  

      char far \*Comment,  

      char far \*InternetAddress,  

      char far \*ProfileName,  

      char far \*LocalAdminName,  

      REGFlags  Flags,  

      REGFlagsExt  FlagsExt,  

      WORD  MinPasswordLength,  

      NOTEHANDLE far \*phUserNote,  

      DBHANDLE far \*phUserNoteNAB,  

      REGSIGNALPROC  signalstatus,  

      char far \*ErrorPathName,  

      void far \*Reserved,  

      void far \*Spare**);**



**Description :**



This
function registers a new workstation.  It performs three functions, each of
which can be selected separately by setting the appropriate flag in the
REGFlags word:  (1)  Create and certify a user's ID file; (2)  Create a mail
file on the user's specified mail server; and (3)  Add or modify the user's
person record in the Domino Directory on the registration server.  It will open
the Domino Directory on the specified registration server, verify write access
to the book, and look for the EntryName specified.  If the user is found, an
error will be returned unless the caller has specified in the REGFlags word
that the user entry may be modified.  If the ID file is found, an error will be
returned unless the caller has specified that it may be modified (overwritten).


 


 


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

  

  

RegUserNameInfo  -  A pointer to the REG\_USERNAME\_INFO structure.  Please see
REG\_USERNAME\_INFO.  

  

RegMailInfo  -  A pointer to the REG\_MAIL\_INFO structure.  Please See REG\_MAIL\_INFO.  

  

Password  -  (Optional).  The password for the new user (workstation).  

  

pGroupList  -  (Optional).  A pointer to a list of groups to add the new user
to, constructed with ListAllocate and ListAddEntries.  Specify NULL if the user
is not to be added to any groups.  

  

IDFileName  -  The pathname of the ID file for the new user (workstation).  If
the fREGCreateIDFileNow flag is not specified, then this file must exist in
order to create a mail file and/or add or modify the user's person record in
the Domino Directory.  Specify NULL for this parameter to have the IDFile
attached to the Person record in the N&A Book (attached file name defaults
to UserID).  

  

  

Location  -  (Optional).  The location of the workstation (used to help in
identification if there is more than one with the same name).    Do not pass in
a literal constant.  

  

Comment  -  (Optional).  Any additional identifying information to be stored in
the Address book or Domino Directory.  

  

  

InternetAddress  -  A pointer to the internet address of the new user.  

  

ProfileName  -  (Optional).  Setup profile name(s).  

  

LocalAdminName  -  (Optional).  The name of the local administrator.  

  

Flags  -  Flags that are set to specify options.  See Symbolic Value, fREGxxx,
in this reference.  

  

FlagsExt  -  Flags that are set to specify options.  See Symbolic Value,
fREGExtxxx, in this reference.  

  

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

  

phUserNote  -  Returns a pointer to the note handle of the new person document
if the caller has specified the REGExtFlag fREGExtReturnPersonNote.  Please see
fREGExtxxx.  

  

phUserNoteNAB  -  Returns a handle to the user note in the NAB.  

  

ErrorPathName  -  (Optional).  Pathname of file where file system error
occurred.  

  

Reserved  -  Reserved for future use.  

  

Spare  -  Reserved for future use.  

  




 **See Also :**


**[fREGExtxxx](fREGExtxxx.md)**


**[fREGxxx](fREGxxx.md)**


**[ListAllocate](ListAllocate.md)**


**[REGNewWorkstationExtended](REGNewWorkstationExtended.md)**


**[REG\_MAIL\_INFO](REG_MAIL_INFO.md)**


**[REG\_USERNAME\_INFO](REG_USERNAME_INFO.md)**



----------------------------------------------------------------------------------------------------------


 





