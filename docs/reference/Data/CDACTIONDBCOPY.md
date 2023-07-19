##### Data Type : Agents
##### CDACTIONDBCOPY - Database Copy action CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;
   DWORD dwFlags;      /* flags */
   WORD  wServerLen;   /* length of server name */
   WORD  wDatabaseLen; /* length of database filespec */
	 /* server name follows */
  /* database filespec follows */
} CDACTIONDBCOPY;

**Description :**

A CDACTIONDBCOPY record is stored in fields of type TYPE_ACTION, usually the action field of an Agent.  When the agent containing this action is run, a copy of the data selected by the agent is placed in the named database.  The fields in this structure are:
<ul><br>

<ul>Header		Defines this composite data item as a CDACTIONDBCOPY item.<br>
dwFlags	Option flags (see ACTIONDBCOPY_FLAG_xxx)<br>
wServerLen	Length of the server name<br>
wDatabaseLen	Length of the database name</ul>
<br>
This structure is followed by packed strings containing the server name and database name.</ul>



**See Also :**
[ACTIONDBCOPY_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACTIONDBCOPY_FLAG_xxx)
---
