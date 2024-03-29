##### Data Type : Notes/FX data
##### DOC_ACTION_INFO - Data structure used to pass document action information via Notes/FX.
---
```
#include <olenotes.h>
```

**Definition :**
```
typedef struct {
   int  ActionID;  /* Notes magic cookie identifying this action */
   WORD NameLength;/* Length of action name string */
   char Name[ACTION_NAME_SIZE]; /* Action name in LMBCS charset */
   DWORD Flags;    /* ACTION_FLAG_xxx */
} DOC_ACTION_INFO;
```

**Description :**

This is the structure of the Notes Document Actions passed through the hDocActions handle in the NOTES_DOC_INFO_MSG to those OLE objects registered as supporting the NotesDocAction SetData() format.   It is an array of the following data structure, whose count is provided in the cNumDocActions member of the NOTES_DOC_INFO_MSG. This data block must be deallocated by the OLE server. 
<ul><br>
<br>
Notes provides the OLE server application with an arbitrary number which is used to identify the action to Notes.  This is referred to internally as a &quot;magic cookie&quot;;  it is similar in use to a handle.  Notes also supplies a character string with the name of the action;  this string is specified in the form definition.<br>
<br>
The fields in this structure are:<br>
<br>
ActionID - Action ID number used by the OLE server application to identify the desired action to Notes.<br>
<br>
NameLength - Number of bytes in the action name string.<br>
<br>
Name - Character array containing the action name string.<br>
<br>
Flags - Control flags for this action;  for the supported flags, see the entry for ACTION_FLAG_xxx.</ul>



**See Also :**
[NSFDbReopen](/domino-c-api-docs/reference/Func/NSFDbReopen)
[NOTES_DOC_INFO_MSG](/domino-c-api-docs/reference/Data/NOTES_DOC_INFO_MSG)
[ACTION_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACTION_FLAG_xxx)
---
