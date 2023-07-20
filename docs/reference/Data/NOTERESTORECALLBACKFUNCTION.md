##### Data Type : Backup
##### NOTERESTORECALLBACKFUNCTION - Definition of the note restore callback function that the backup/archive utility will have to provide for monitoring notes during Media Recovery.
---
```
#include <nsfdb.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR NOTERESTORECALLBACKFUNCTION)( 
	DWORD state_flags, 
	void far * userParm, 
	NOTE_RESTORE_CALLBACK_INFO far * info);
```

**Description :**

During media recovery, this callback function is implemented with the following parameters:  
<ul>
<ul><br>
inputs:
<ul>
<ul>state_flags - The state flag which describes the action taken on a particular note during the media recovery process.  See MediaCallbackFlags.<br>
<br>
userParm - User information (e.g.  NoteID, UserName, etc.) supplied to NSFRecoverDatabasesWIthCallback to be passed to NOTERESTORECALLBACKFUNCTION  to narrow the scope of the callback routine.  Zero to return information for all notes updated. <br>
<br>
info - Pointer to the structure which contains information regarding each note updated during the media recovery process.  See NOTE_RESTORE_CALLBACK_INFO.</ul>
</ul>
<br>
outputs:	
<ul>
<ul>STATUS - Status of the call: NOERROR. Any other status indicates an error condition.</ul>
</ul>
</ul>
</ul>



**See Also :**
[MediaCallbackFlags](/domino-c-api-docs/reference/Data/MediaCallbackFlags)
[NOTE_RESTORE_CALLBACK_INFO](/domino-c-api-docs/reference/Data/NOTE_RESTORE_CALLBACK_INFO)
[NSFRecoverDatabasesWithCallback](/domino-c-api-docs/reference/Func/NSFRecoverDatabasesWithCallback)
---
