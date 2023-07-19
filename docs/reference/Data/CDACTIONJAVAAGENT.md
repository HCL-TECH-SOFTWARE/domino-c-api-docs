##### Data Type : Agents
##### CDACTIONJAVAAGENT - Java agent action CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;
   WORD  wClassNameLen;  /* Agent name length */
   WORD  wCodePathLen;
   WORD  wFileListBytes;
   WORD  wLibraryListBytes;
   WORD  wSpare[1];
   DWORD dwSpare[1];
/* Strings follow */
} CDACTIONJAVAAGENT;

**Description :**

A CDACTIONJAVAAGENT record is stored in fields of type TYPE_ACTION, usually the action field of an Agent.  This record identifies the Java class files that will be executed when the agent is run.  The fields in this structure are:
<ul><br>
<br>
Header			Defines this composite data item as a CDACTIONJAVAAGENT item.<br>
wClassNameLen		Length of the Java class name (the class to be invoked).<br>
wCodePathLen		Length of the Java code pathname.<br>
wFileListBytes		Length of the Java class file list.<br>
wLibraryListBytes		Length of the shared Java Library list.<br>
<br>
This structure is followed by the three strings, stored asLMBCS strings with no NULL delimiter.  The Java class files are stored as $FILE items in the document;  the Java class file name is the file name of the $FILE item.</ul>



**See Also :**
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---
