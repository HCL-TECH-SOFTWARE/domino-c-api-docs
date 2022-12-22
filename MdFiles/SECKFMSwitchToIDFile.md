




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



**Function : IDs; User**



**SECKFMSwitchToIDFile** **- Switch to
a new ID.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECKFMSwitchToIDFile(**  

      char \*pIDFileName,  

      char \*pPassword,  

      char \*pUserName,  

      WORD  MaxUserNameLength,  

      DWORD  Flags,  

      void \*pReserved**);**



**Description :**



This
function switches to the specified ID file and returns the user name associated
with it.  Multiple passwords are not supported.


 


NOTE: This
function should only be used in a C API stand alone application.


 


**Parameters :**



Input :  

pIDFileName  -  Points to a null-terminated string containing the path to the
ID file that is to be switched to.  

  

pPassword  -  Points to a null-terminated string containing the password of the
ID file that is to be switched to.  

  

MaxUserNameLength  -  Maximum length of buffer pointed to by pUserName.  

  

Flags  -  Optional, may be set to 0.  See fKFM\_switchid\_xxx.  If
fKFM\_switchid\_DontSetEnvVar is not specified, the notes.ini file (either
ServerKeyFileName or KeyFileName) is modified to reflect the ID change.  

  

pReserved  -  Reserved, should be set to NULL.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.   The return codes include:  

  

NOERROR - Action successful.  

  

ERR\_NOEXIST - The ID file specified does not exist.  

  

ERR\_BSAFE\_BADPASSWORD - The password specified is incorrect.  

  

ERR\_BSAFE\_TOOSMALL - The MaxUserNameLength specified is too small.  

  

ERR\_BSAFE\_SUBPROCESS - A sub-process cannot change to a new ID file or prompt
for passwords.  

  

ERR\_xxx  -  Various OS, and KFM errors.  Call to OSLoadString to interpret the
error status as a string that you may display/log for the user.  

  

  

pUserName  -  Points to a buffer where the user name, in the ID file that is to
be switched to, will be returned.  

  




 **See Also :**


**[fKFM\_switchid\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A4609EB90F6F011485256E670054EA6E)**



----------------------------------------------------------------------------------------------------------


 





