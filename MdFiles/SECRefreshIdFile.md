




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



**Function : Address Book**



**SECRefreshIdFile** **- Refresh
an ID file.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECRefreshIdFile(**  

      char \*pIDFileName,  

      char \*pPassword,  

      char \*pServer,  

      DWORD \*retFlags,  

      DWORD  Reserved,  

      void \*pReserved**);**



**Description :**



This routine
will search the $USERS view of the name and address book (directory) on the
specified server for the user name extracted out of the ID file.  If a unique
match is found, then a check for Notes certificate changes, Internet
certificate changes and user name changes is made.  If updates are allowed to
be pulled into the ID file then they will be.  It will be up to the user to
re-attach the ID file to where it is stored using either NSFNoteAttachFile or
SECAttachIdFileToDB.


 


**Parameters :**



Input :  

pIDFileName  -  Name of ID file to be refreshed with certificate and name
changes.  

  

pPassword  -  Password to the ID file to be refreshed.  

  

pServer  -  Server whose name and address book (directory) is to be searched
for user name, which was pulled from the ID file, for updates to Notes
certificates, Internet certificates and name changes.  

  

Reserved  -  Reserved, should be set to 0.  

  

pReserved  -  Reserved, should be set to NULL.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.   The return codes include:  

  

NOERROR - action successful  

  

  

retFlags  -  Return flags indicating what has changed.  See SEC\_refreshed\_xxx.  

  




 **See Also :**


**[SECAttachIdFileToDB](SECAttachIdFileToDB.md)**


**[SECKFMClose](SECKFMClose.md)**


**[SECKFMOpen](SECKFMOpen.md)**


**[SEC\_refreshed\_xxx](SEC_refreshed_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





