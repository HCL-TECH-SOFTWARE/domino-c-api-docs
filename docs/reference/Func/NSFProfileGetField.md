##### Function : Profile Document
##### NSFProfileGetField - Get the value of the field in a profile document.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFProfileGetField(

	DBHANDLE  hDB,
	const char *ProfileName,
	WORD  ProfileNameLength,
	const char *UserName,
	WORD  UserNameLength,
	const char *FieldName,
	WORD  FieldNameLength,
	WORD *retDatatype,
	BLOCKID *retbhValue,
	DWORD *retValueLength);
```
**Description :**

Get the value of the field in a profile document.  The profile document is 
opened automatically if it is not already open. 

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

UserNameLength  -  Length of the user name.  Optional - may be zero.

FieldName  -  Name of the field of which to get the value.

FieldNameLength  -  Length of the field name.

Output :
(routine)  -  NOERROR - Successfully returned the field wanted from the profile document.
ERR_xxx - Use OSLoadString to display the error returned.


retDatatype  -  Datatype of the item.

retbhValue  -  BLOCKID pointing to the value of the item, including the datatype word.

retValueLength  -  Length of the value of the item, including the datatype word.


**Sample Usage :**
```
char UserName[]="John Doe";
char FieldBuffer[128];
char *pData;
 
/* Open the database. */
    
if (error = NSFDbOpen (path_name, &db_handle))
{
 print_api_error (error);
	NotesTerm();
 exit (EXIT_FAILURE);
}

/* Get the "Owner" item from "John Doe's" "CalendarProfile" document */

if( error = NSFProfileGetField( db_handle, MAIL_CALENDAR_PROFILE_FORM,
	      (WORD) strlen(MAIL_CALENDAR_PROFILE_FORM),
       UserName, (WORD) strlen(UserName),
       MAIL_CALENDAR_PROFILE_OWNER_ITEM,
       (WORD) strlen(MAIL_CALENDAR_PROFILE_OWNER_ITEM),
       &retDataType,
       &retbhValue,
       &retValueLength))
{
 print_api_error (error);
	NSFDbClose( db_handle );
 NotesTerm();
 exit (EXIT_FAILURE);
}

if( retDataType == TYPE_TEXT )
{
	pData = OSLockBlock( char, retbhValue );
 pData += sizeof(WORD);     /* step over data type word */

	memmove( FieldBuffer, pData, (int) (retValueLength - sizeof(WORD)));
 FieldBuffer[retValueLength - sizeof(WORD)] = '\0';
 OSUnlockBlock( retbhValue);

	printf("\nValue of Field Requested is %s.\n", FieldBuffer);
}

```
**See Also :**
[NSFProfileSetField](/domino-c-api-docs/reference/Func/NSFProfileSetField)
---
