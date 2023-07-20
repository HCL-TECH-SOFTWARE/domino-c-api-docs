##### Data Type : Agents
##### CDACTIONNEWSLETTER - Generate Newsletter action CD record.
---
```
#include <queryods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header;
   DWORD dwFlags;      /* flags */
   DWORD dwGather;     /* gather at least n documents */
   WORD  wViewNameLen; /* View to use to display data */
   WORD  wSpare;
   WORD  wFieldLen[ACTIONSENDMAIL_FIELDCOUNT];
	 /* View name follows */
	 /* To field follows */
  /* cc field follows */
  /* bcc field follows */
  /* Subject field follows */
	 /* Body field follows */
} CDACTIONNEWSLETTER;
```

**Description :**

A CDACTIONNEWSLETTER record is stored in fields of type TYPE_ACTION, usually the action field of an Agent.  When the agent containing this action is run, a &quot;newsletter&quot; is generated.  A newsletter consists of a doclink to each note identified by the query segment of this Agent.  The fields in this structure are:
<ul><br>

<ul>Header		Defines this composite data item as a CDACTIONNEWSLETTER item.<br>
dwFlags	Option flags (see ACTIONNEWSLETTER_FLAG_xxx).<br>
dwGather	Minimum number of documents to gather.<br>
wViewNameLen  Length, in bytes, of the name of the view used to display the data<br>
wSpare		Reserved;  must be 0.<br>
wFieldLen	Array of lengths for the send mail fields</ul>
<br>
This record is followed by the string values for the view name and the send mail fields, in packed format (no NULL terminators).  The strings contain:<br>

<ul>ViewName	Name of view used to display the data<br>
To		Recipient list<br>
cc		Courtesy copy recipient list<br>
bcc		&quot;Blind&quot; courtesy copy recipient list<br>
Subject		Message subject<br>
Body		Message body</ul>
<br>
<b>Note:</b>  Newsletter formula flags are the same as sendmail flags, so do not use the ACTIONSENDMAIL_FLAG_xxx flag values for newsletter flags.</ul>



**See Also :**
[ACTIONNEWSLETTER_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACTIONNEWSLETTER_FLAG_xxx)
[ACTIONSENDMAIL_xxx](/domino-c-api-docs/reference/Symb/ACTIONSENDMAIL_xxx)
---
