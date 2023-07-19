##### Data Type : Agents
##### CDQUERYBYFOLDER - Query by Folder query CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG Header;
   DWORD dwFlags;       /* Flags */
   WORD wFolderNameLen; /* Length of folder name */
	 /* Folder name follows */
} CDQUERYBYFOLDER;

**Description :**

Folder queries are stored in CDQUERYBYFOLDER records in fields of type TYPE_QUERY, usually the query field of an Agent.  This query selects the contents of a folder to be operated on by the Agent.  This record consists of this data structure followed by the folder name.  The fields in this structure are:
<ul><br>

<ul>Header		Defines this composite data item as a CDQUERYBYFOLDER item.<br>
dwFlags		Folder query flags (see QUERYBYFOLDER_FLAG_xxx).<br>
wFolderNameLen	Length of the folder name.</ul>
<br>
This structure is followed by a packed string containing the folder name.</ul>



**See Also :**
[QUERYBYFOLDER_FLAG_xxx](/domino-c-api-docs/reference/Symb/QUERYBYFOLDER_FLAG_xxx)
---
