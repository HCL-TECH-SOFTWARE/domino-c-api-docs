




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



**Function : Profile Document**



**SECAttachIdFileToDB** **- Attach an
ID file to a profile note.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECAttachIdFileToDB(**  

      DBHANDLE  hDB,  

      char \*pProfileNoteName,  

      DWORD  ProfileNoteNameLength,  

      char \*pUserName,  

      DWORD  UserNameLength,  

      char \*pIDFileName,  

      char \*pPassword,  

      DWORD  Reserved,  

      void \*pReserved**);**



**Description :**



This routine
will search the database for a named profile note and, if the note exists, will
delete any ID File attachments present, get the input ID file in a roamed state
and attach it to the record.  If the note does not exists, it will create the
note, get the input ID file in a roamed state and attach it to the named
record.


 


**Parameters :**



Input :  

hDB  -  Open database handle of database to have the ID file attached to in
"roamed" state.  

  

pProfileNoteName  -  Profile note name that the ID file will be attached to.  

  

ProfileNoteNameLength  -  Length of the profile note name.  

  

pUserName  -  Name of user requesting access to the profile note.  Should be
NULL.  

  

UserNameLength  -  Length of user name.  Should be zero.  

  

pIDFileName  -  Name of ID file to be "roamed" and attached to the
pProfileNoteName in the database.  

  

pPassword  -  Password to the ID file to be roamed and attached to the
pProfileNoteName in the database.  

  

Reserved  -  Reserved, should be set to 0.  

  

pReserved  -  Reserved, should be set to NULL.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.   The return codes include:  

  

NOERROR - action successful  

  

  




 **See Also :**


**[SECKFMClose](SECKFMClose.md)**


**[SECKFMOpen](SECKFMOpen.md)**



----------------------------------------------------------------------------------------------------------


 





