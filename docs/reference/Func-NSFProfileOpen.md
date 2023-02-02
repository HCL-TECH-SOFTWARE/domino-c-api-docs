##### Function : Profile Document
##### NSFProfileOpen - Open a profile document.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFProfileOpen(**

	DBHANDLE  hDB,
	const char *ProfileName,
	WORD  ProfileNameLength,
	const char *UserName,
	WORD  UserNameLength,
	BOOL  CopyProfile,
	NOTEHANDLE *rethProfileNote);
**Description :**
Open a profile document.  If a profile for the specified profile name/user pair 
does not exist, one is created.  Author access is the minimum access required 
to create a profile document.
**Parameters :**
Input :
hDB  -  Handle to the database where the profile document exists or is to be created.

ProfileName  -  Name of the profile.

ProfileNameLength  -  Length of the profile name.

UserName  -  Name of the user of this profile.  Optional - may be NULL.
Note:  Author access is the minimum access required to create a profile document.  With author access one can create profiles without a user name specified; create profiles with a different user name specified; or create profiles with their own user name specified.  For each profile document created, the UserName is contained in a TYPE_TEXT field named $Name.  This $Name field is represented as "prefix_nnnprofilename_username" where:
     prefix = the type of document
     nnn = 3 digit character representation of the length of the profile name
     profilename = the name of the profile document
     username = the UserName of the profile
An example of this field from a "Calendar Profile" document created from the Notes client would be, $profile_015calendarprofile_.  Here the UserName is blank since this profile was created with the Notes client.  Therefore to retrieve this profile, use NULL for UserName.  Another example of a profile document where UserName may be blank is the "Delegation Profile".  This profile is also created using the Notes client.

UserNameLength  -  Length of the user name.  Optional - may be zero

CopyProfile  -  Must be TRUE.  The handle to a copy of the cached profile document is returned.

Output :
(routine)  -  NOERROR - Successfully returned the handle to the profile document.
ERR_xxx - Use OSLoadString to display the error returned.


rethProfileNote  -  Handle to the profile document.  The caller is responsible for closing the returned note handle when done with the note.

**Sample Usage :**
```
char UserName[]="John Doe";

/* Open the database. */
    
if ( Error = NSFDbOpen (path_name, &hDB))
{
 fprintf( stderr, "Error encountered opening the database.\n");
      LAPI_RETURN( ERR(Error));
}

/* Open the "CalendarProfile" Document for user "John Doe" */

if( Error = NSFProfileOpen( db_handle,
        MAIL_CALENDAR_PROFILE_FORM,(WORD) strlen(MAIL_CALENDAR_PROFILE_FORM),
        UserName,(WORD) strlen(UserName),
        TRUE, &note_handle))
{
	fprintf( stderr, "Error encountered opening this Profile Document.\n");
	NSFDbClose( hDB );
      LAPI_RETURN( ERR(Error));
}
```
**See Also :**
[NSFProfileDelete](D:/md_files/NSFProfileDelete.md)
[NSFProfileUpdate](D:/md_files/NSFProfileUpdate.md)
---
