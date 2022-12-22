




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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



**Function : User**



**SECKFMChangePassword** **- Change
the password in the specified ID file.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECKFMChangePassword(**  

      char far \*pIDFile,  

      char far \*pOldPassword,  

      char far \*pNewPassword**);**



**Description :**



This
function changes the password in the specified ID file. You can use this
function to change the password in a user's id, a server's id, or a certifier's
id.  Multiple passwords are not supported.


 


**Parameters :**



Input :  

pIDFile  -   Points to a null-terminated string containing the path to the ID
file whose password should be changed.    

  

For example, you can use OSGetEnvironmentString with the VariableName set to
"KeyFileName" to obtain the path to the current user's ID file.  

  

If this parameter is set to "", then ERR\_BSAFE\_NULLPARAM is returned.  

  

pOldPassword  -  Points to a null-terminated string containing the old password
in the ID file.  This parameter can only be NULL if there is no old password. 
If this parameter is set to "", then ERR\_BSAFE\_NULLPARAM is returned.  

  

pNewPassword  -  Points to a null-terminated string containing the new password
on the ID file. If this parameter is NULL, the password is cleared.  If the
specified ID file requires a password and this parameter is NULL, then
ERR\_BSAFE\_PASSWORD\_REQUIRED is returned.  If this parameter is set to
"", then ERR\_BSAFE\_NULLPARAM is returned.  If the specified ID file
is set for a minimum password length and this string contains less than that
minimum, then ERR\_REG\_MINPSWDCHARS is returned.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.   The return codes include:  

  

NOERROR - action successful  

  

ERR\_BSAFE\_NULLPARAM - Illegal parameter.  One of the input parameters is set to
the empty ("") string.  

  

ERR\_BSAFE\_PASSWORD\_REQUIRED - A password is required for the specified ID file.  

  

ERR\_SECURE\_NOKEYFILE - Could not open the ID file.  

  

ERR\_REG\_MINPSWDCHARS - More or varied characters needed for new password.  

  

ERR\_xxx  -  Various OS, and KFM errors.  Call to OSLoadString to interpret the
error status as a string that you may display/log for the user.  

  

  




 **Sample Usage :**


STATUS  error;        
/\* error code from API calls \*/  

char    \*pIDFile;  

char    \*OrigPassword;  

char    \*NewPassword;  

char    IDFileSpec[MAXENVVALUE+1];


 


error =
NotesInitExtended (argc, argv);


 


if (error)  

{  

   printf ("\nError initializing Notes.\n");  

   return();  

}


 


/\* Get the
current user's id file path specification \*/


 


if
(!OSGetEnvironmentString ("KeyFileName", IDFileSpec, MAXENVVALUE))  

{  

    printf ("Cannot locate current id file, using NULL for
pIDFile\n");


   
NotesTerm();


   
return();  

}


 


if (error =
SECKFMChangePassword (pIDFile, OrigPassword, NewPassword))  

{  

   print\_api\_error (error);  

   NotesTerm();  

   return();  

}


 **See Also :**


**[SECKFMGetUserName](SECKFMGetUserName.md)**


**[SECKFMUserInfo](SECKFMUserInfo.md)**



----------------------------------------------------------------------------------------------------------


 





