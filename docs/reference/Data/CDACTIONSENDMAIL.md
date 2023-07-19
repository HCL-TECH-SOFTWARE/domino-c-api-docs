##### Data Type : Agents
##### CDACTIONSENDMAIL - Send Mail action CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;
   DWORD dwFlags; /* flags */
   WORD  wFieldLen[ACTIONSENDMAIL_FIELDCOUNT]; /* Lengths for each of
                                                  the fields */
	 /* To field follows */
  /* cc field follows */
  /* bcc field follows */
  /* Subject field follows */
	 /* Body field follows */
} CDACTIONSENDMAIL;

**Description :**

The Send Mail action is stored in a CDACTIONSENDMAIL record in fields of type TYPE_ACTION, usually the action field of an Agent.  The fields in this structure are:
<ul><br>

<ul><tt><font size="2">Header &nbsp; &nbsp; SIG_ACTION_SENDMAIL and total record length</font></tt><br>
<tt><font size="2">dwFlags &nbsp; &nbsp;ACTIONSENDMAIL_FLAG_xxx flags</font></tt><br>
<tt><font size="2">wFieldLen &nbsp;Array of lengths for the send mail fields</font></tt></ul>
<br>
This record is followed by the string values for the send mail fields.  These strings are <b><u>not</u></b> in packed format;  each string has a NUL terminator, and may contain a padding byte if necessary to make the length an even number of bytes.  The strings contain:<br>

<ul>To		Recipient list<br>
Cc		Courtesy copy recipient list<br>
Bcc		&quot;Blind&quot; courtesy copy recipient list<br>
Subject		Message subject<br>
Body		Message body</ul>
</ul>



**See Also :**
[ACTIONSENDMAIL_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACTIONSENDMAIL_FLAG_xxx)
[ACTIONSENDMAIL_xxx](/domino-c-api-docs/reference/Symb/ACTIONSENDMAIL_xxx)
---
