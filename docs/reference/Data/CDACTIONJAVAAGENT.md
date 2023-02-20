##### Data Type : Agents
##### CDACTIONJAVAAGENT - Java agent action CD record.
---
```
#include <queryods.h>
```
**Description :**

A CDACTIONJAVAAGENT record is stored in fields of type TYPE_ACTION, usually the 
action field of an Agent.  This record identifies the Java class files that 
will be executed when the agent is run.  The fields in this structure are:

Header   Defines this composite data item as a CDACTIONJAVAAGENT item.
wClassNameLen  Length of the Java class name (the class to be invoked).
wCodePathLen  Length of the Java code pathname.
wFileListBytes  Length of the Java class file list.
wLibraryListBytes  Length of the shared Java Library list.

This structure is followed by the three strings, stored asLMBCS strings with no 
NULL delimiter.  The Java class files are stored as $FILE items in the 
document;  the Java class file name is the file name of the $FILE item.

**See Also :**
[CDACTION](/reference/Data/CDACTION)
---