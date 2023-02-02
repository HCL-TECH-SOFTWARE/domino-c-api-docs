##### Function : Profile Document
##### NSFProfileUpdate - Update an open profile document.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFProfileUpdate(**

	NOTEHANDLE  hProfile,
	const char *ProfileName,
	WORD  ProfileNameLength,
	const char *UserName,
	WORD  UserNameLength);
**Description :**
Update an open profile document.  The items in the cached note for this profile 
document are replaced with the items in the specified profile note.  In 
addition, the database is updated using the specified profile note.  The caller 
is responsible for closing the handle to the profile document after the update.
**Parameters :**
Input :
hProfile  -  Handle of the profile document to be updated.

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
(routine)  -  NOERROR - Successfully updated the profile document.
ERR_xxx - Use OSLoadString to display the error returned.


**Sample Usage :**
```
char ProfileName[]="MyProfile";
char UserName[]="John Doe";


/* Open "MyProfile" Document for User John Doe.*/

if( error = NSFProfileOpen( db_handle,
        ProfileName,(WORD) strlen(ProfileName),
        UserName,(WORD) strlen(UserName),
        TRUE, &note_handle))
{
 print_api_error (error);
 NSFDbClose( db_handle );
	NotesTerm();
 exit (EXIT_FAILURE); 
}

NSFNoteGetInfo( note_handle, _NOTE_ID, &note_id );
printf("\nProfile Note ID %lX \n", note_id );

/* Set field ProfileOwner to the value in UserName */

if( error = NSFItemSetText( note_handle, "ProfileOwner", 
        UserName, (WORD) strlen(UserName)))
{
 print_api_error (error);
	NSFNoteClose( note_handle );
	NSFDbClose( db_handle );
 NotesTerm();
 exit (EXIT_FAILURE);
}

/* Update this Profile Document with the new information */

if( error = NSFProfileUpdate( note_handle, ProfileName,
      (WORD) strlen(ProfileName),
     UserName, (WORD) strlen(UserName)))
{
 print_api_error (error);
	NSFNoteClose( note_handle );
	NSFDbClose( db_handle );
 NotesTerm();
 exit (EXIT_FAILURE);
}

/* Close the note_handle to this Profile Document */
NSFNoteClose( note_handle );
```
**See Also :**
[NSFProfileOpen](D:/md_files/NSFProfileOpen.md)
---
