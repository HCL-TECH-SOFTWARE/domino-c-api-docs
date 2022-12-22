




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
 /\* List Definitions \*/
 ol
 {margin-bottom:0cm;}
ul
 {margin-bottom:0cm;}
-->




**Initial Release 7.0**



**Function : Backup; Database; DB2**



**NSFDB2RegenerateLinks** **- Verify
that all link files exist on the Domino server's data directory.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDB2RegenerateLinks(**  

      DWORD  flags**);**



**Description :**



This
function can be used after a DB2 database restore to make sure that all link
files exist on the Domino server's data directory.   This function can also be
used if a Domino server's data directory was erased and restored from a
NSF-specific backup in order to regenerate the link files for all DB2 Domino data.   
This function can also be used to verify that links to NSFDB2 databases are
valid.


 


Notes:


*       
This function can only be run on the Domino server when the server
is down.


*       
Actions taken by this API call will be logged.


 


**Parameters :**



Input :  

flags  -  See DB2BACKUP\_LINKS\_xxx.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successful.  

  

ERR\_DB2BACKUP\_SERVERRUNNING - The Domino server cannot be running when this
command executes.  

  

ERR\_DB2NSF\_CLI\_ERROR - Internal DB2/CLI error.  

  

ERR\_DB2NSF\_NOT\_ENABLED\_FOR\_DB2 - The Domino server is not enabled for DB2.  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  




 **See Also :**


**[DB2BACKUP\_LINKS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/193E1DE2C5D55C564825705F0044C234)**


**[NSFDB2GetInfo](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/406189AFDCB6E04385256E60004A00D1)**


**[NSFDB2GetServerInfo](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F4041BDF22D5C4B585256E60004CAE77)**


**[NSFDB2ListNSFDB2Databases](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A57AF7CF730AA01685256E6000560BE5)**


**[NSFDB2ReconnectNotesDatabase](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F551E2856602672185256E600054B6EC)**



----------------------------------------------------------------------------------------------------------


 





