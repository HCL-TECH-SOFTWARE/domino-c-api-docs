##### Data Type : Agents
##### CDACTIONNEWSLETTER - Generate Newsletter action CD record.
---
```
#include <queryods.h>
```
**Description :**

A CDACTIONNEWSLETTER record is stored in fields of type TYPE_ACTION, usually 
the action field of an Agent.  When the agent containing this action is run, a 
"newsletter" is generated.  A newsletter consists of a doclink to each note 
identified by the query segment of this Agent.  The fields in this structure 
are:

Header  Defines this composite data item as a CDACTIONNEWSLETTER item.
dwFlags Option flags (see ACTIONNEWSLETTER_FLAG_xxx).
dwGather Minimum number of documents to gather.
wViewNameLen  Length, in bytes, of the name of the view used to display the data
wSpare  Reserved;  must be 0.
wFieldLen Array of lengths for the send mail fields

This record is followed by the string values for the view name and the send 
mail fields, in packed format (no NULL terminators).  The strings contain:

ViewName Name of view used to display the data
To  Recipient list
cc  Courtesy copy recipient list
bcc  "Blind" courtesy copy recipient list
Subject  Message subject
Body  Message body

Note:  Newsletter formula flags are the same as sendmail flags, so do not use 
the ACTIONSENDMAIL_FLAG_xxx flag values for newsletter flags.

**See Also :**
[ACTIONNEWSLETTER_FLAG_xxx](/reference/Symb/ACTIONNEWSLETTER_FLAG_xxx)
[ACTIONSENDMAIL_xxx](/reference/Symb/ACTIONSENDMAIL_xxx)
---
