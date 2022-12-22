




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



**Function : Database; DB2**



**NSFDB2PutUsernamePW** **- Store a
DB2 username and password in a Notes ID file.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



  

STATUS LNPUBLIC **NSFDB2PutUsernamePW(**  

      char \*ServerName,  

      char \*pFilename,  

      char \*UserName,  

      char \*Password,  

      KFM\_PASSWORD \*pKfmPW**);**



**Description :**



This
function will store a DB2 username and password in a specified Notes ID file.


 


**Parameters :**



Input :  

ServerName  -  Pointer to a null-terminated character string containing the
name of the server on which the ID resides.  NULL for local.  

  

pFilename  -  Pointer to a null-terminated character string containing the name
of the user ID to put the user's DB2 username and password.  NULL if current ID
is to be used.  

  

UserName  -  Pointer to a null-terminated character string containing the name
of the DB2 user to store in the ID.  

  

Password  -  Pointer to a null-terminated character string containing the
password of the DB2 user to store in the ID.  

  

pKfmPW  -  Pointer to the encoded password structure containing the user's
hashed password.  NULL if current ID is in use or no password.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **See Also :**


**[KFM\_PASSWORD](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/12C436308A3BC570852562060075B641)**


**[NSFDB2DeleteUsernamePW](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E4450D50AF2A320385256EBD0047CC10)**


**[NSFDB2GetUsernamePW](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/EECEF8A84ECDF6C185256EBD00447C5A)**


**[SECKFMCreatePassword](SECKFMCreatePassword.md)**



----------------------------------------------------------------------------------------------------------


 





