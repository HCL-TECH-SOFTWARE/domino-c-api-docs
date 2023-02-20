##### Function : Profile Document
##### NSFProfileEnum - Enumerates profile documents with the specified profile name.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFProfileEnum(

	DBHANDLE  hDB,
	const char *ProfileName,
	WORD  ProfileNameLength,
	NSFPROFILEENUMPROC  Callback,
	void *CallbackCtx,
	DWORD  Flags);
```
**Description :**

Enumerates through all profile documents in the database which have the 
specified profile name.  If the given profile is found then the function calls 
a user-supplied routine (an action routine) for that profile. 

**Parameters :**
Input :
hDB  -  Handle to the database where the profile document exists.

ProfileName  -  Name of the profile.  To enumerate all profile documents within a database, use NULL for ProfileName.

ProfileNameLength  -  Length of the profile name.

Callback  -  Enumeration routine to process each profile that is found.

CallbackCtx  -  Caller defined context block that is passed to the enumeration routine.  Optional, may be NULL.

Flags  -  (Reserved for future use.)  Must be 0.

Output :
(routine)  -  NOERROR - No errors occurred through the execution of NSFProfileEnum or any of the calls to the action routine.
ERR_xxx - Use OSLoadString to display the error returned.



**Sample Usage :**
```
/* Open the database. */
    
if (Error = NSFDbOpen (path_name, &hDB))
{
 fprintf( stderr, "Error encountered opening the database.\n");
	PrintAPIError (Error);  
	NotesTerm();
	return (1);
}
/* 
 * Enumerate all "CalendarProfile" Documents for this Database. 
 * Action Routine DumpProfile() will be called for each "CalendarProfile"
 * document found.
 */
if (Error = NSFProfileEnum( hDB, MAIL_CALENDAR_PROFILE_FORM,
	       (WORD) strlen(MAIL_CALENDAR_PROFILE_FORM),
        DumpProfile, NULL, 0 ))
{
 fprintf( stderr, "Error encountered searching for profile information.\n");
	NSFDbClose( hDB );
	PrintAPIError (Error);  
	NotesTerm();
	return (1);
}
```
**See Also :**
[NSFPROFILEENUMPROC](/reference/Data/NSFPROFILEENUMPROC)
---
