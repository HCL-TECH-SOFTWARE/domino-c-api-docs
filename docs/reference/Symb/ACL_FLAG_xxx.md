##### Symbolic Value : Access Control List
##### ACL_FLAG_xxx - Access level modifier flags.
---
```
#include <acl.h>
```

**Symbolic Values :**

	ACL_FLAG_AUTHOR_NOCREATE	  -  User has access level of author and cannot create new notes (can only edit existing ones).

	ACL_FLAG_SERVER	  -  Entry represents a Server

	ACL_FLAG_NODELETE	  -  User cannot delete notes.

	ACL_FLAG_CREATE_PRAGENT	  -  User can create personal agents

	ACL_FLAG_CREATE_PRFOLDER	  -  User can create personal folders

	ACL_FLAG_PERSON	  -  Entry represents a Person

	ACL_FLAG_GROUP	  -  Entry represents a group

	ACL_FLAG_CREATE_FOLDER	  -  User can create and update shared views & folders. This allows an Editor to assume some Designer-level access

	ACL_FLAG_CREATE_LOTUSSCRIPT	  -  User can create LotusScript

	ACL_FLAG_PUBLICREADER	  -  User can read public notes

	ACL_FLAG_PUBLICWRITER	  -  User can write public notes

	ACL_FLAG_ADMIN_SERVER	  -  Entry is administration server

	ACL_FLAG_MONITORS_DISALLOWED	  -  User cannot register headline monitors for this database.

	ACL_FLAG_NOREPLICATE	  -  User cannot replicate or copy this database.


**Description :**

These symbols represent access level modifier flags in access control lists.  Each access level taken by itself implies a certain set of immutable capabilities. Each access level has a different set of access modifier bits that are relevant for that level.  All of the other bits that are returned in the Access Flag parameter of C API functions are irrelevant and are unpredictable. The table below depicts which Access Level Modifier Flags (ACL_FLAG_xxx) are applicable to the Access Levels (ACL_LEVEL_xxx).<br>
<div align="center"></div><br>

<table border="1">
<tr valign="top"><td width="192"><div align="center"><b>ACL_LEVEL_xxx</b></div></td><td width="288"><div align="center"><b>ACL_FLAG_xxx Applicable </b><br>
<b>to ACL_LEVEL_xxx</b></div></td></tr>

<tr valign="top"><td width="192">
<ul>ACL_LEVEL_MANAGER</ul>
</td><td width="288">
<ul>ACL_FLAG_NODELETE<br>
ACL_FLAG_PERSON<br>
ACL_FLAG_GROUP<br>
ACL_FLAG_SERVER</ul>
</td></tr>

<tr valign="top"><td width="192">
<ul>ACL_LEVEL_DESIGNER</ul>
</td><td width="288">
<ul>ACL_FLAG_NODELETE<br>
ACL_FLAG_CREATE_LOTUSSCRIPT<br>
ACL_FLAG_PERSON<br>
ACL_FLAG_GROUP<br>
ACL_FLAG_SERVER</ul>
</td></tr>

<tr valign="top"><td width="192">
<ul>ACL_LEVEL_EDITOR</ul>
</td><td width="288">
<ul>ACL_FLAG_NODELETE<br>
ACL_FLAG_CREATE_PRAGENT<br>
ACL_FLAG_CREATE_PRFOLDER<br>
ACL_FLAG_CREATE_FOLDER<br>
ACL_FLAG_CREATE_LOTUSSCRIPT<br>
ACL_FLAG_PERSON<br>
ACL_FLAG_GROUP<br>
ACL_FLAG_SERVER</ul>
</td></tr>

<tr valign="top"><td width="192">
<ul>ACL_LEVEL_AUTHOR</ul>
</td><td width="288">
<ul>ACL_FLAG_AUTHOR_NOCREATE<br>
ACL_FLAG_NODELETE<br>
ACL_FLAG_CREATE_PRAGENT<br>
ACL_FLAG_CREATE_PRFOLDER<br>
ACL_FLAG_CREATE_LOTUSSCRIPT<br>
ACL_FLAG_PUBLICWRITER<br>
ACL_FLAG_PERSON<br>
ACL_FLAG_GROUP<br>
ACL_FLAG_SERVER</ul>
</td></tr>

<tr valign="top"><td width="192">
<ul>ACL_LEVEL_READER</ul>
</td><td width="288">
<ul>ACL_FLAG_CREATE_PRAGENT<br>
ACL_FLAG_CREATE_PRFOLDER<br>
ACL_FLAG_CREATE_LOTUSSCRIPT<br>
ACL_FLAG_PUBLICWRITER<br>
ACL_FLAG_PERSON<br>
ACL_FLAG_GROUP<br>
ACL_FLAG_SERVER</ul>
</td></tr>

<tr valign="top"><td width="192">
<ul>ACL_LEVEL_DEPOSITOR</ul>
</td><td width="288">
<ul>ACL_FLAG_PUBLICREADER<br>
ACL_FLAG_PUBLICWRITER<br>
ACL_FLAG_PERSON<br>
ACL_FLAG_GROUP<br>
ACL_FLAG_SERVER</ul>
</td></tr>

<tr valign="top"><td width="192">
<ul>ACL_LEVEL_NOACCESS</ul>
</td><td width="288">
<ul>ACL_FLAG_PUBLICREADER<br>
ACL_FLAG_PUBLICWRITER<br>
ACL_FLAG_PERSON<br>
ACL_FLAG_GROUP<br>
ACL_FLAG_SERVER</ul>
</td></tr>
</table>



**See Also :**
[ACLLookupAccess](/domino-c-api-docs/reference/Func/ACLLookupAccess)
[ACLAddEntry](/domino-c-api-docs/reference/Func/ACLAddEntry)
[ACLUpdateEntry](/domino-c-api-docs/reference/Func/ACLUpdateEntry)
[ACLEnumEntries](/domino-c-api-docs/reference/Func/ACLEnumEntries)
[NSFDbAccessGet](/domino-c-api-docs/reference/Func/NSFDbAccessGet)
---
