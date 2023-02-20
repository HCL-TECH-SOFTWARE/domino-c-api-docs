##### Data Type : Backup
##### NOTERESTORECALLBACKFUNCTION - Definition of the note restore callback function that the backup/archive utility will have to provide for monitoring notes during Media Recovery.
---
```
#include <nsfdb.h>
```
**Description :**

During media recovery, this callback function is implemented with the following 
parameters:  

inputs:
state_flags - The state flag which describes the action taken on a particular 
note during the media recovery process.  See MediaCallbackFlags.

userParm - User information (e.g.  NoteID, UserName, etc.) supplied to 
NSFRecoverDatabasesWIthCallback to be passed to NOTERESTORECALLBACKFUNCTION  to 
narrow the scope of the callback routine.  Zero to return information for all 
notes updated. 

info - Pointer to the structure which contains information regarding each note 
updated during the media recovery process.  See NOTE_RESTORE_CALLBACK_INFO.

outputs: 
STATUS - Status of the call: NOERROR. Any other status indicates an error 
condition.

**See Also :**
[MediaCallbackFlags](/reference/Data/MediaCallbackFlags)
[NOTE_RESTORE_CALLBACK_INFO](/reference/Data/NOTE_RESTORE_CALLBACK_INFO)
[NSFRecoverDatabasesWithCallback](/reference/Func/NSFRecoverDatabasesWithCallback)
---
