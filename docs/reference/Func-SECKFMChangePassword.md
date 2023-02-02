##### Function : User
##### SECKFMChangePassword - Change the password in the specified ID file.
---
##### #include <kfm.h>
STATUS LNPUBLIC **SECKFMChangePassword(**

	char far *pIDFile,
	char far *pOldPassword,
	char far *pNewPassword);
**Description :**
This function changes the password in the specified ID file. You can use this 
function to change the password in a user's id, a server's id, or a certifier's 
id.  Multiple passwords are not supported.
**Parameters :**
Input :
pIDFile  -   Points to a null-terminated string containing the path to the ID file whose password should be changed.  

For example, you can use OSGetEnvironmentString with the VariableName set to "KeyFileName" to obtain the path to the current user's ID file.

If this parameter is set to "", then ERR_BSAFE_NULLPARAM is returned.

pOldPassword  -  Points to a null-terminated string containing the old password in the ID file.  This parameter can only be NULL if there is no old password.  If this parameter is set to "", then ERR_BSAFE_NULLPARAM is returned.

pNewPassword  -  Points to a null-terminated string containing the new password on the ID file. If this parameter is NULL, the password is cleared.  If the specified ID file requires a password and this parameter is NULL, then ERR_BSAFE_PASSWORD_REQUIRED is returned.  If this parameter is set to "", then ERR_BSAFE_NULLPARAM is returned.  If the specified ID file is set for a minimum password length and this string contains less than that minimum, then ERR_REG_MINPSWDCHARS is returned.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is.   The return codes include:

NOERROR - action successful

ERR_BSAFE_NULLPARAM - Illegal parameter.  One of the input parameters is set to the empty ("") string.

ERR_BSAFE_PASSWORD_REQUIRED - A password is required for the specified ID file.

ERR_SECURE_NOKEYFILE - Could not open the ID file.

ERR_REG_MINPSWDCHARS - More or varied characters needed for new password.

ERR_xxx  -  Various OS, and KFM errors.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


**Sample Usage :**
```
STATUS  error;         /* error code from API calls */
char    *pIDFile;
char    *OrigPassword;
char    *NewPassword;
char    IDFileSpec[MAXENVVALUE+1];

error = NotesInitExtended (argc, argv);

if (error)
{
   printf ("\nError initializing Notes.\n");
   return();
}

/* Get the current user's id file path specification */

if (!OSGetEnvironmentString ("KeyFileName", IDFileSpec, MAXENVVALUE))
{
    printf ("Cannot locate current id file, using NULL for pIDFile\n");
    NotesTerm();
    return();
}

if (error = SECKFMChangePassword (pIDFile, OrigPassword, NewPassword))
{
   print_api_error (error);
   NotesTerm();
   return();
}
```
**See Also :**
[SECKFMGetUserName](D:/md_files/SECKFMGetUserName.md)
[SECKFMUserInfo](D:/md_files/SECKFMUserInfo.md)
---
