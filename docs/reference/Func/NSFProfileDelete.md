##### Function : Profile Document
##### NSFProfileDelete - Delete a profile document.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFProfileDelete(

	DBHANDLE  hDB,
	const char *ProfileName,
	WORD  ProfileNameLength,
	const char *UserName,
	WORD  UserNameLength);
```
**Description :**

Delete a profile document from the database. 

**Parameters :**
Input :
hDB  -  Handle to the database where the profile document exists.

ProfileName  -  Name of the profile.

ProfileNameLength  -  Length of the profile name.

UserName  -  Name of the user of this profile.  Optional - may be NULL.
Note:  For each profile document created, the UserName is contained in a TYPE_TEXT field named $Name.  This $Name field is represented as "prefix_nnnprofilename_username" where:
     prefix = the type of document
     nnn = 3 digit character representation of the length of the profile name
     profilename = the name of the profile document
     username = the UserName of the profile
An example of this field from a "Calendar Profile" document created from the Notes client would be, $profile_015calendarprofile_.  Here the UserName is blank since this profile was created with the Notes client.  Therefore to retrieve this profile, use NULL for UserName.  Another example of a profile document where UserName may be blank is the "Delegation Profile".  This profile is also created using the Notes client.

UserNameLength  -  Length of the user name.  Optional - may be zero

Output :
(routine)  -  NOERROR - Successfully deleted the profile document.
ERR_xxx - Use OSLoadString to display the error returned.



**Sample Usage :**
```
char UserName[]="John Doe";

/* Open the database. */
    
if (error = NSFDbOpen (path_name, &db_handle))
{
 print_api_error (error);
	NotesTerm();
 exit (EXIT_FAILURE);
}

/* Delete the "CalendarProfile" for John Doe from this database */

if( error = NSFProfileDelete( db_handle, MAIL_CALENDAR_PROFILE_FORM,
	    (WORD) strlen(MAIL_CALENDAR_PROFILE_FORM), UserName, 
(WORD)strlen(UserName)))
{
 print_api_error (error);
	NSFDbClose( db_handle );
 NotesTerm();
 exit (EXIT_FAILURE);
}

```
**See Also :**
[NSFProfileOpen](/domino-c-api-docs/reference/Func/NSFProfileOpen)
[NSFProfileUpdate](/domino-c-api-docs/reference/Func/NSFProfileUpdate)
---
